---
title: "can't record audio"
date: 2010-05-24
forum: Hardware
---

### Post by kamedin on 2010-05-24
I'm running Ubuntu Studio 10 for amd64 (Linux 2.6.32-22-preempt, ALSA 1.0.22, PulseAudio 0.9.22, GStreamer 0.10.28 ). My sound card is a Realtek ALC888.

All tries to record audio with Audacity have failed (the cursor attempts to move but keeps fixed at the startpoint). With gnome-sound-recorder, sometimes the first two or three tries work. Then, at some point every try fails in the same way (the cursor doesn't move and nothing is recorded).

Now I run gnome-sound-recorder with --gst-debug-level=5, and when recording fails, all output is freezed to a sequence of these:

0:01:05.751176868  1801      0x152e180 LOG                    pulse pulsesrc.c:547:gst_pulsesrc_stream_latency_update_cb:<autoaudiosrc1-actual-src-puls> latency_update, 1274728700390709000, 0:0, 0:0, 0, 46000
0:01:05.832666983  1801      0x152e180 LOG                    pulse pulsesrc.c:547:gst_pulsesrc_stream_latency_update_cb:<autoaudiosrc1-actual-src-puls> latency_update, 1274728700472126000, 0:0, 0:0, 0, 46000
0:01:05.992713162  1801      0x152e180 LOG                    pulse pulsesrc.c:547:gst_pulsesrc_stream_latency_update_cb:<autoaudiosrc1-actual-src-puls> latency_update, 1274728700632148000, 0:0, 0:0, 0, 46000

Something similar affects jackd (whenever I set analog duplex instead of playback only, I get a cascade of xruns before the server dies).

---

