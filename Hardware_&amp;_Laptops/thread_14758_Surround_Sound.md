---
title: "Surround Sound"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by apokryphos on 2005-02-09
Ever since moving to Ubuntu, I haven't been able to get full use out of all the speakers. Only two seem to provide any Audio output; the speakers in general work, and they have so on several Linux distros, Windoze etc.. without any particular configuration. 

Any idea how I could get the whole sound system to work? Audio info from lspci just in case it comes in handy:
> 0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
Any help would be greatly appreciated.

---

### Post by ember on 2005-02-09
[QUOTE=apokryphos]Ever since moving to Ubuntu, I haven't been able to get full use out of all the speakers. Only two seem to provide any Audio output; the speakers in general work, and they have so on several Linux distros, Windoze etc.. without any particular configuration. 

Any idea how I could get the whole sound system to work? Audio info from lspci just in case it comes in handy:

Any help would be greatly appreciated.[/QUOTE]
 As far as I know, the Nvidia sound drivers support only OSS which has only two channels in the free version. So I'm afraid there won't be any sound on the rest of the speaker as long as there is an alsa-driver for the Soundstorm-Chip.

---

### Post by apokryphos on 2005-02-09
I really don't see how it can be down to OSS (if that's what you're saying), considering I was previously using OSS on Fedora and it was all running swell; unless Fedora has the non-free version, which seems doubtful to me, but I really have no idea.

---

### Post by zeroz52 on 2005-02-27
apokryphos:  Did you have to install the nforce linux drivers?  I ask cause I have no sound at all.  

0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008

---

### Post by apokryphos on 2005-03-19
Nope, didn't install anything extra for them to work as they are.

---

