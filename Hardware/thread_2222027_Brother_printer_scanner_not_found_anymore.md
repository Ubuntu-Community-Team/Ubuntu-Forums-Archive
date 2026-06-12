---
title: "Brother printer scanner not found anymore"
date: 2014-05-04
forum: Hardware
---

### Post by phillyj on 2014-05-04
I used to be able to scan with my Brother HL-2280DW but not anymore. I had everything installed last year, but I think a recent update borked it. I can still print but simple-scan or xsane won't detect a scanner. Please help me figure out how to solve this. I looked at explainations from other people with a similar problem but they don't help me. I'm hooked up via wireless, if that matters.

---

### Post by gifford on 2014-05-04
Had a similar problem with my MFC-495CW. The issue was that I had also changed routers and the ip address of the printer had changed. The Brother scanner requires that you name the ip address of the scanner when setting it up so if it has changed the scanner won't be detected by scan or xsane.

---

### Post by QIII on 2014-05-04
;)   lol!

Just as an aside ....  In American English idiom, the term you used in your OP is a "cutesy" word for an intimate act between two consenting adults.  It is not quite considered *vulgar*, but please be careful of the Forums CoC.  We have folks from all sorts of cultural backgrounds and levels of tolerance for vulgarity, so we require that everything be kept family friendly.

If you are looking for the term more associated with Techies with regard to systems that have been messed up, you may be searching for the word "borked" -- which is derived from the failed Senate confirmation of Robert Bork to the US Supreme Court.

I've edited your post to replace that word.  I'm not perceiving this as an attempt to circumvent the CoC's rules regarding vulgarity, so no blood/no foul!

Best wishes.

---

### Post by phillyj on 2014-06-15
Ok, so I'm trying to figure out this network business (of which I have no idea about). I looked into my router and compared the printer IP address, and it looks same.

Router is 192.168.2.1 and printer is 192.168.2.10

The confusing thing is that I can print from this computer with no problems. I will check if another PC on the network can scan.

---

### Post by phillyj on 2014-06-15
Alright, so I figured it out. It turns out that I had to re-register the device. Some change must have occured. Maybe the IP address did change but was not updated for the scanner settings?

To fix it, I ran the command "brsaneconfig4  -a  name=Scanner  model=HL-2280DW  ip=192.168.2.10" from terminal and it came back to normal. Now I can scan without a problem

---

### Post by kurt18947 on 2014-06-15
> **phillyj said:**
> Alright, so I figured it out. It turns out that I had to re-register the device. Some change must have occured. Maybe the IP address did change but was not updated for the scanner settings?

To fix it, I ran the command "brsaneconfig4  -a  name=Scanner  model=HL-2280DW  ip=192.168.2.10" from terminal and it came back to normal. Now I can scan without a problem

I don't have that printer, I have 2 Brother MFCs which have numeric keypads.  I find it makes my life simpler to assign a static I.P. address to the printer.  I use the numeric keypad on the ours, it appears your machine does not have a numeric keypad.  I'm sure there's a way to assign a static I.P. address, I just don't know what that way is.

---

