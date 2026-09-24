# Dialog-RSN-1 voice agent in Python

The full example from [Build a voice agent from scratch with Python](https://dialog-rsn-1-eap-docs.pages.dev/dialog-rsn-1/guides/python-from-scratch/).
The guide explains every part of it. This repo is the finished file, ready to run.

A terminal voice agent on the standard `websockets` package, with no SDK. It streams microphone audio in,
lets the server detect turns, calls tools, and prints each reply as text.

## Run it

You need Python 3.10 or later and a Dialog-RSN-1 API key.

```bash
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env        # add your DIALOGUE_API_KEY
set -a && . ./.env && set +a

python voice_agent.py                                    # open the mic and talk
python voice_agent.py --say "What time is it right now?" # one text turn, no mic needed
```

`--say` sends a single text turn and exits once the reply is done. Use it to check your key and the
tool calls before you try the microphone.

## What's in it

| File | What it is |
|---|---|
| `voice_agent.py` | The guide's full example, unchanged |
| `requirements.txt` | `websockets>=14`, `sounddevice`, `numpy` |
| `.env.example` | The one variable the script reads, `DIALOGUE_API_KEY` |

`websockets` 14 renamed `extra_headers` to `additional_headers`, so older versions fail at `connect()`.

## Related

- [Dialog-RSN-1 quickstart](https://dialog-rsn-1-eap-docs.pages.dev/dialog-rsn-1/quickstart/)
- [Dialog-RSN-1 reference](https://dialog-rsn-1-eap-docs.pages.dev/dialog-rsn-1/reference/)
- [Browser version of this agent](https://github.com/polyai/dialog-rsn-1-javascript-browser)

## License

Apache 2.0. See [LICENSE](LICENSE).
