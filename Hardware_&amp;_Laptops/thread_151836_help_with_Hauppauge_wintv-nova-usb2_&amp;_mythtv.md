---
title: "help with Hauppauge wintv-nova-usb2 &amp; mythtv"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by basiel on 2006-03-28
Hi all,

I got my Hauppauge wintv-nova-USB2 card working. I also installed mythtv without any problems. I streamed my settings to mplayer and indeed got the channel i wanted. I configured my mythTV backend with the correct channels, it has +-70% signal strength so that is looking good also. But when i try to watch via my mythtvfrontend i get the following output:

2006-03-29 00:01:05.429 New DB connection, total: 1
Total desktop width=1024, height=768, numscreens=1
2006-03-29 00:01:05.462 Using screen 0, 1024x768 at 0,0
2006-03-29 00:01:05.469 mythfrontend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-03-29 00:01:05.469 Enabled verbose msgs : important general
2006-03-29 00:01:05.755 Switching to square mode (G.A.N.T.)
2006-03-29 00:01:06.205 Registering Internal as a media playback plugin.
2006-03-29 00:01:09.596 New DB connection, total: 2
2006-03-29 00:01:09.642 Connecting to backend server: 192.168.1.2:6543 (try 1 of 5)
2006-03-29 00:01:09.662 Using protocol version 15
2006-03-29 00:01:09.728 Using protocol version 15
2006-03-29 00:01:14.924 taking too long to be allowed to read..
2006-03-29 00:01:19.929 taking too long to be allowed to read..
2006-03-29 00:01:28.943 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:32.952 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:36.956 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:40.964 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:44.968 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:48.977 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:52.981 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:56.989 Waited 4 seconds for data to become available, waiting again...
2006-03-29 00:01:56.989 Waited 14 seconds for data to become available, aborting
Couldn't read file: rbuf://192.168.1.2:6543/mnt/store//ringbuf1.nuv
2006-03-29 00:01:57.067 Changing from None to WatchingLiveTV
2006-03-29 00:01:57.067 Decoder not alive, and trying to play..
2006-03-29 00:01:57.577 RemoteFile::Read() failed in RingBuffer::safe_read().
2006-03-29 00:01:57.581 Changing from None to None


Anyone got any idea how to solve this problem?

Thanks
Filip

---

