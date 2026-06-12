---
title: "graphic memory"
date: 2008-07-08
forum: Hardware
---

### Post by ettercap on 2008-07-08
hello every 1
i hav an hp pavilion laptop having 8400m gs (128 MB dedicated memory) using ubuntu 8.04
i want to set my graphic memory to 128 mb
where do i set it....
and also i cannot access my BIOS because it is password protected
( actually i entered the incorrect password 3 times !! :mad:) 
so i need to change it the GUI way .......
even the terminal way will do...........

plz help 
thanks

---

### Post by sdennie on 2008-07-08
If you mean an nvidia 8400M GS, you can't change the video memory.  It's dedicated memory on the graphics card.  To verify that it's all there, try:

```

nvidia-settings -q VideoRam

```

There appears to be a bug with the nvidia drivers where it may be reporting double the actual memory available (reported on at least 2 nvidia cards on Dell machines).

---

