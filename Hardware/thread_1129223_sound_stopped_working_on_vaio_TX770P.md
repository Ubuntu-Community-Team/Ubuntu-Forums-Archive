---
title: "sound stopped working on vaio TX770P"
date: 2009-04-18
forum: Hardware
---

### Post by Keith_Beef on 2009-04-18
For some strange reason, sound has stopped working in Ubuntu 8.10 on my Sony Vaio TX770P.

It had been working find for months, then I noticed it was no longer working.

This didn't bother me at first, since the tiny little speakers are not much good, anyway. But now I'm back at home, I wanted to play back through the aux input of the living-room stereo again.

I tried looking in the audio volume controls, nothing is muted.
I looked in the sound settings, and tried the different devices listed.

No joy.

I wonder if recent updates have broken the sound?

below is a list of recent updates.

```
$ more /var/log/dpkg.log | grep installed
2009-04-04 09:53:13 status half-installed tzdata 2009c-0ubuntu0.8.10
2009-04-04 09:53:14 status half-installed tzdata 2009c-0ubuntu0.8.10
2009-04-04 09:53:19 status installed tzdata 2009d-0ubuntu0.8.10
2009-04-04 09:53:21 status half-installed libldap-2.4-2 2.4.11-0ubuntu6.1
2009-04-04 09:53:22 status half-installed libldap-2.4-2 2.4.11-0ubuntu6.1
2009-04-04 09:53:22 status half-installed libldap-2.4-2 2.4.11-0ubuntu6.1
2009-04-04 09:53:22 status half-installed libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-04-04 09:53:23 status half-installed libssl0.9.8 0.9.8g-10.1ubuntu2.1
2009-04-04 09:53:26 status half-installed doc-base 0.8.16
2009-04-04 09:53:26 status half-installed doc-base 0.8.16
2009-04-04 09:53:26 status half-installed doc-base 0.8.16
2009-04-04 09:53:27 status half-installed foo2zjs 20080810-0ubuntu4
2009-04-04 09:53:27 status half-installed foo2zjs 20080810-0ubuntu4
2009-04-04 09:53:28 status half-installed foo2zjs 20080810-0ubuntu4
2009-04-04 09:53:29 status half-installed libsndfile1 1.0.17-4
2009-04-04 09:53:29 status half-installed libsndfile1 1.0.17-4
2009-04-04 09:53:30 status half-installed openssl 0.9.8g-10.1ubuntu2.1
2009-04-04 09:53:30 status half-installed openssl 0.9.8g-10.1ubuntu2.1
2009-04-04 09:53:30 status half-installed openssl 0.9.8g-10.1ubuntu2.1
2009-04-04 09:53:31 status half-installed xserver-xorg-video-intel 2:2.4.1-1ubuntu10.3
2009-04-04 09:53:31 status half-installed xserver-xorg-video-intel 2:2.4.1-1ubuntu10.3
2009-04-04 09:53:31 status half-installed xserver-xorg-video-intel 2:2.4.1-1ubuntu10.3
2009-04-04 09:53:34 status installed man-db 2.5.2-2
2009-04-04 09:53:35 status installed libldap-2.4-2 2.4.11-0ubuntu6.2
2009-04-04 09:53:38 status installed libssl0.9.8 0.9.8g-10.1ubuntu2.2
2009-04-04 09:53:39 status installed doc-base 0.8.16ubuntu1
2009-04-04 09:53:40 status installed foo2zjs 20080810-0ubuntu4.1
2009-04-04 09:53:40 status installed libsndfile1 1.0.17-4ubuntu0.8.10.1
2009-04-04 09:53:40 status installed openssl 0.9.8g-10.1ubuntu2.2
2009-04-04 09:53:40 status installed xserver-xorg-video-intel 2:2.4.1-1ubuntu10.4
2009-04-04 09:53:40 status installed libc6 2.8~20080505-0ubuntu9
2009-04-07 01:21:15 status half-installed linux-image-2.6.27-11-generic 2.6.27-11.27
2009-04-07 01:21:38 status half-installed linux-image-2.6.27-11-generic 2.6.27-11.27
2009-04-07 01:21:47 status half-installed linux-headers-2.6.27-11 2.6.27-11.27
2009-04-07 01:21:57 status half-installed linux-headers-2.6.27-11 2.6.27-11.27
2009-04-07 01:22:14 status half-installed linux-headers-2.6.27-11-generic 2.6.27-11.27
2009-04-07 01:22:17 status half-installed linux-headers-2.6.27-11-generic 2.6.27-11.27
2009-04-07 01:22:44 status installed linux-image-2.6.27-11-generic 2.6.27-11.31
2009-04-07 01:22:44 status installed linux-headers-2.6.27-11 2.6.27-11.31
2009-04-07 01:22:45 status installed linux-headers-2.6.27-11-generic 2.6.27-11.31
2009-04-07 22:22:32 status half-installed libkrb53 1.6.dfsg.4~beta1-3
2009-04-07 22:22:32 status half-installed libkrb53 1.6.dfsg.4~beta1-3
2009-04-07 22:22:33 status half-installed libpq5 8.3.7-0ubuntu8.10
2009-04-07 22:22:33 status half-installed libpq5 8.3.7-0ubuntu8.10
2009-04-07 22:22:36 status installed libkrb53 1.6.dfsg.4~beta1-3ubuntu0.1
2009-04-07 22:22:36 status installed libpq5 8.3.7-0ubuntu8.10.1
2009-04-07 22:22:36 status installed libc6 2.8~20080505-0ubuntu9

```

Anybody else experience similar problems recently? More importantly, anybody got any suggestions for fixing it?


K.

---

