---
title: "The Anti-Telemarketer; intercepting incoming calls with a Linux computer and a modem"
date: 2008-11-14
forum: General Help
---

### Post by Ironchew on 2008-11-14
I wasn't exactly sure where to put this, so I put it here.
I want to defend myself against telemarketers, especially robo-calls, and I know I have the technology at my fingertips to accomplish this.  I've worked out a relatively simple plan for intercepting incoming land-line calls *before* the phone rings:

1.  Play a pre-recorded message that tells the caller to enter a random sequence of numbers to prove they're a human.
2.  The caller enters the sequence, possibly 4 digits, and a DTMF program recognizes the correct sequence.
3.  If they don't do anything, or if the robo-call starts its message, the program hangs up the line after about 5 seconds.
4.  If the sequence is correct, the call goes through and the phone rings.

Something like this would make a telephone more of a utility and less of an annoyance, especially during a campaign season when we (in the United States) are being constantly bombarded with robo-calls!  I just started reading up about Asterisk, an open-source PBX server, but I don't want to route multiple calls to multiple phones.  I have one (cordless) phone, and I just want to intercept all calls to my house.  Any Linux gurus that can point me in the right direction with software/hardware to use?  (Can Asterisk do the job?  Can I use a simple modem or two?)  I am fairly experienced with Linux administration and I'm not afraid of the terminal.  Thanks for any replies.

---

### Post by gpsmikey on 2008-11-14
Not exactly what you want, but still worth checking out -- after careful thought, I finally figured out how the "robo-dialers" determine if they got a real person (which they then transfer to a "sales associate") or an answering machine (which they promptly hang up on).  It's all about timing - an answering machine goes "hello, we're not here right now .... " while a live person tends to go "hello" and wait for a response.  The trick is to program your answering machine with an outgoing message of "hello ... (pause 3 seconds) .. we're not here right now ... ".  Absolutely amazing how many messages we find on the answering machine like "hello ?  Hello ?? anybody there ?? damn!" and then they hang up.  Worth it just to be a pain to them - it wastes their time !! :lolflag:

mikey

---

### Post by HermanAB on 2008-11-14
A nice and simple idea indeed.

---

### Post by CLomax on 2008-11-14
Make this available for the UK too and I'll love you forever. We have a problem with robo-calls here too :(

---

### Post by igknighted on 2008-11-14
There's a national do not call list... sign your number up and if you keep getting calls they are breaking the law

---

### Post by scouser73 on 2008-11-14
Here's the line for the Telephone Preference Service
[http://www.mpsonline.org.uk/tps/]("http://www.mpsonline.org.uk/tps/")

---

### Post by Dubbayoo on 2008-11-14
We have VOIP at work and we get A LOT of robocalls. The weird thing is it's already talking before I pick up the phone.

---

### Post by CLomax on 2008-11-14
Awesome, thanks for the info and link. :)

---

### Post by jjthomas on 2008-12-28
The problem with Asterisk is that is does not work with Plain Old Telephone Service lines.

Take a look at VOCP at [http://www.vocpsystem.com/](http://www.vocpsystem.com/)  I've built a system with Mandrivia 2009, P-III and a US Robotics 56K Voice Modem.  Seems to work as advertised.  

-JJ

---

### Post by hyper_ch on 2008-12-28
you might want to have a look at Asterisk:  [http://www.asterisk.org/](http://www.asterisk.org/)

---

### Post by jjthomas on 2008-12-29
> **jjthomas said:**
> The problem with Asterisk is that is does not work with Plain Old Telephone Service lines.

Take a look at VOCP at [http://www.vocpsystem.com/](http://www.vocpsystem.com/)  I've built a system with Mandrivia 2009, P-III and a US Robotics 56K Voice Modem.  Seems to work as advertised.  

-JJ

To clarify, Asterisk will work with POTS, but you need specilized (telecommunications) hardware to make it work.  I set mine up with VOCP and a US Robotics Modem. :)

---

