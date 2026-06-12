---
title: "What is wrong with my modprobe.conf?"
date: 2008-08-16
forum: General Help
---

### Post by yojimba on 2008-08-16
I'm documenting trying to get a tuner card to work under another thread where I had posted the question below in the thread but have had no response. I hope it's okay to post my question here in hope of getting some feedback . . . 

Is there something I might have done incorrectly in adding the three lines at the bottom of my modprobe.conf below?  Could there be conflicts with what I've added and what is under # bttv since both are referencing alias char-major-81? 

I've been spending hours researching this and have hit a wall . . .

modprobe.conf file
>>>>>>>>>>>>>>>>>>>>>

# i2c
alias char-major-89 i2c-dev
options i2c-core i2c_debug=1
options i2c-algo-bit bit_test=1

# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
options bttv card=2 radio=1
options tuner debug=1

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90

>>>>>>>>>>>>>>>>>>>>>>>>>>

---

