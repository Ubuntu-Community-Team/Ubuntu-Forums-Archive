---
title: "ubuntu dummy output - Just show the HDMI cards not analog"
date: 2022-03-05
forum: Hardware
---

### Post by ali-reza on 2022-03-05
How to problem occurs:
I was watching a course and suddenly my laptop rebooted and after that, I have no sound and 'Dummy output' Showed to me.
I tried almost all google solutions and none of them working, I would like to figure out the problem and make it work, Anyone is here can help me with this?

`aplay -l` output: [https://pastebin.ubuntu.com/p/X3M23w6b4d/](https://pastebin.ubuntu.com/p/X3M23w6b4d/)
`pacmd list-cards` output: [https://pastebin.ubuntu.com/p/CGss74Dt4n/](https://pastebin.ubuntu.com/p/CGss74Dt4n/)
`pacmd list-sinks` output: [https://pastebin.ubuntu.com/p/ntX3wWDKN2/](https://pastebin.ubuntu.com/p/ntX3wWDKN2/)
`pulseaudio -vvv` output: [https://pastebin.ubuntu.com/p/JN2vz4Pq8Z/](https://pastebin.ubuntu.com/p/JN2vz4Pq8Z/)

As you see in logs (aplay output) is just HDMI cards, not my main card and PulseAudio says: pa_pid_file_create() failed.

---

