---
title: "ATI CrossFire Does Not Support On This Platform When Enabling"
date: 2010-07-12
forum: Hardware
---

### Post by hayhursm on 2010-07-12
[SIZE=3]I recently installed the ATI Catalyst Driver 8.74 and Catalyst Control Center 10.6 in Ubuntu Lucid.  Upon enabling the CrossFire link I received this message in the terminal: 
[B]CrossFire chain(s) enabled
CrossFire does not support on this platform

[/B]But when I run the command **sudo aticonfig --lsch **I get
**CrossFire chain for adapter 0, status: enabled **and then it lists my adapters in the CrossFire chain.

I thought the last message meant CrossFire is working but because of the first message I have my doubts...does anyone know why the terminal says CrossFire is enabled but still say CrossFire does not support this platform?  Any help is appreciated.
[/SIZE]

---

### Post by hayhursm on 2010-07-13
bump

---

### Post by Twitch6000 on 2010-07-13
It says it is enabled. So I do not see an issue,but I have never used ati. So to get a confirmed answer you will need to wait for an ati user.

---

### Post by hayhursm on 2010-07-13
> **Twitch6000 said:**
> It says it is enabled. So I do not see an issue,but I have never used ati. So to get a confirmed answer you will need to wait for an ati user.

I agree but I just stumbled across some new information.  "aticonfig --lscs" list the CrossFire status (which I guess is apparently different than the chain status (aticonfig --lsch)???  And that states that the "CrossFire is disabled on the current device".  It also says CrossFire can work with P2P mapping through GART, so do I maybe have to go this route?  Thanks for the help...it's difficult to get any response in Ubuntu forums.

---

### Post by hayhursm on 2010-07-16
BUMP
 
 
Also stumbled across this in terminal:


user@desktop:~$ sudo aticonfig --lsa
* 0. 01:00.0 ATI Radeon HD 3870
1. 04:00.0 ATI Radeon HD 3870

* - Default adapter
user@desktop:~$ aticonfig --lscc

Master adapter: 0. 01:00.0 ATI Radeon HD 3870
Candidates: none
user@desktop:~$ aticonfig --odgt

Default Adapter - ATI Radeon HD 3870
Sensor 0: Temperature - 43.00 C
user@desktop:~$ aticonfig --odgc

Default Adapter - ATI Radeon HD 3870
Core (MHz) Memory (MHz)
Current Clocks : 300 1126
Current Peak : 776 1126
Configurable Peak Range : [300-885] [1126-1387]
GPU load : 0%
user@desktop:~$ aticonfig --odgc --adapter=1
ERROR - Get clocks failed for Adapter 1 - ATI Radeon HD 3870
user@desktop:~$ aticonfig --odgt --adapter=1
ERROR - Get temperature failed for Adapter 1 - ATI Radeon HD 3870



Is this a good indication that something is wrong with adapter 1 graphics card since the "aticonfig --odgt and --odgc" commands work for adapter 0 but not adapter 1? I cannot get a response from adapter 1 but yet the "aticonfig --lsa" command recognizes it as a working adapter. Has anyone had this sort of problem before? Again, I'm just trying to enable CrossFire.

---

### Post by llawwehttam on 2010-07-16
To put it simply linux and ati do not work well together and its mainly ati's fault. As they do not expect people to game on linux they do not see the need to write drivers for things such as crossfire that work.

---

### Post by hayhursm on 2010-07-16
> **llawwehttam said:**
> To put it simply linux and ati do not work well together and its mainly ati's fault. As they do not expect people to game on linux they do not see the need to write drivers for things such as crossfire that work.
 
 
Hey thank you for the reply!  I was beginning to worry I was alone in this world.  So ATI and Linux are like oil and water right?  What would you suggest?  Is Nvidia the way to go then?  My only complaint is that I have seen others successfully enable CrossFire but maybe my setup is just the wrong combination then?  At this point I'm confused.

---

