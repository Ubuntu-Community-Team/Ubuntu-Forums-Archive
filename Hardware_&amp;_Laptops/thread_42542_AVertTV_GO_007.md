---
title: "AVertTV GO 007"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by peter07 on 2005-06-18
I have big problem with AVER TV GO 007. I don't now how to install this TV/Radio Tunner. Please help.

---

### Post by peter07 on 2005-08-05
More info:

I'm trying to install **AVerTV GO 007 TV/ radio tuner** ( **Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)** ). I've tried:

1) Changes in /etc/modprobe.d/aliases:
 
alias video bttv
options tuner debug=1
options bttv radio=1 pll=1 card=57 bttv_verbose=2 bttv_debug=1
options tuner type=39 pal=b

2) libzvbi0 installation

3) Zapping, tvtime installation

4) sudo modrobe saa7134 ( and sudo modprobe saa7134 card=56 remote=1 radio=1 )

Tv and radio aren't working. When I try to use gradio I get error message:
> 
/dev/radio: No such file or directory   

Please help

---

