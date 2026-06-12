---
title: "lircrc file help"
date: 2008-07-20
forum: General Help
---

### Post by yessit on 2008-07-20
I installed lirc from synaptic and lirc.conf file from lirc.org 

avermedia studio 203 remote: 
some buttons are working already with some of events. (power, numbers, vol up and down)

i want to use it with **mplayer**.
My ~/.lircrc file is shown below but Can't seem to get the remote functions working. 

```
begin
   prog = mplayer
   button = PAUSE
   config = pause
end

begin
   prog = mplayer
   button = ChannelDOWN
   repeat = 3
   config = seek -60
end
begin
   prog = mplayer
   button = ChannelDOWN
   repeat = 3
   config = seek 60
end
begin
   prog = mplayer
   button = VolumeDOWN
   repeat = 2
   config = volume -2
end
begin
   prog = mplayer
   button = VolumeUP
   repeat = 2
   config = volume 2
end
begin
   prog = mplayer
   button = TELETEXT
   config = osd
end
```

---

### Post by yessit on 2008-07-21
solved
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/235811](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/235811)

---

