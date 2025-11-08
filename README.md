# Reliable Message Transfer (Sliding Window) – Client/Server (Python)

> Course Project (Networks)  
> Implements reliable transfer over an unreliable channel: fixed-size encoded packets, sliding windows for **time** and **sequence**, retransmissions, ordered ACKs, and end-of-message handshake.

## ✨ Highlights
- **Package format & codec:** fixed-size `struct.pack/unpack`; header, pos, sent_time, payload; matching decoder.  
- **Windows & retransmissions:** adaptive `TIME_WINDOW` and `SEQ_WINDOW` with threshold checks and resend logic.  
- **Server ACK policy:** ordered ACKs, can intentionally skip ACKs to simulate loss; handles `DONE` to rebuild the message.  
- **Deterministic demos:** reproducible runs for **lost packets** and **lost ACKs**, with Wireshark traces.

## 🗂️ Project Layout
- `client.py` / `server.py` — runtime logic, windows & resend policy  
- `package.py` — packet class + encode/decode + validations  
- `functions.py` — helpers (params, slicing, utilities)  
- `get_packages.py` — parses Wireshark JSON and decodes frames with our codec

## 🚀 Quick Start
```bash
# 1) install
pip install -r requirements.txt

# 2) run server (terminal A)
python server.py

# 3) run client (terminal B)
python client.py --max-msg-size 4   # minimum accepted

# (Optional) use provided params files in /demo to auto-load scenarios
