---
title: "Ubuntu 8.10 on Toshiba Satellite U400-H00"
date: 2008-12-28
forum: Hardware
---

### Post by Olnex on 2008-12-28
I bought Toshiba U400 yesterday, firstly I tried Opensuse 11.1, most of things work out of the box, however, I don't like several aspects of Opensuse, so I installed Ubuntu 8.10 today, and I followed the guide:
[http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn]("http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn")

In the "Fix Things" section, I tried to add omnibook module to enable bluetooth, however, when I add the apt key, I got:
--2008-12-29 11:19:17--  [http://packages.kirya.net/Kirya.netDebianpackagesVerificationKey.asc](http://packages.kirya.net/Kirya.netDebianpackagesVerificationKey.asc)
Resolving packages.kirya.net... 66.246.76.225
Connecting to packages.kirya.net|66.246.76.225|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1946 (1.9K) [text/plain]
Saving to: `STDOUT'

100%[======================================>] 1,946       --.-K/s   in 0.08s   

2008-12-29 11:19:18 (24.3 KB/s) - `-' saved [1946/1946]

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

Then I tried to download the key first, save it in a file, then apt-key add the_file, but it does not work.

Also, the microphone works in Opensuse 11.1 but not work in Ubuntu 8.10, I searched the internet and found out several people complain that their mic(either internal or external) used to be working in 8.04 but not working when using 8.10, in alsa mixer windows, apart from Master and PCM, I have enabled Docking Mic, External Mic and Internal Mic, they are all adjusted to max but the mic does not work, when I record using Sound Recorder, Length increase very fast, several seconds later it becomes several minutes in length.

---

