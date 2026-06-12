---
title: "newb"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by delpgdn on 2009-02-27
im trying to reinstall 8.10 but autorun cd wont work  ?

---

### Post by sukhhari on 2009-02-28
First try to check CD problem and then install ubuntu with F4 options.

---

### Post by tommcd on 2009-02-28
> **delpgdn said:**
> im trying to reinstall 8.10 but autorun cd wont work  ?

Are you trying to install inside Windows using Wubi? Or are you trying to install (the real way) to a dedicated linux partition? Please provide as much info as possible, including what kind of computer you are using and it's specs.

If you are installing to a separate linux partition you must set your computer's BIOS to boot from the CDROM drive. Also, try burning the CD at the slowest possible speed. Try burning with Iso Recorder or Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
If you are installing using Wubi follow this tutorial:
[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

---

### Post by delpgdn on 2009-03-01
thank you for help still working on problem

---

### Post by tommcd on 2009-03-03
> **delpgdn said:**
> thank you for help still working on problem

Can you tell us what the problem is? As I said in my last post, please try to provide as much info as possible, including:
1. Specs of your computer, including motherboard chipset if you know it.
2. How are you installing Ubuntu? Wubi? or from the live CD to a dedicated partition?

When you said "but autorun cd wont work", if you are trying to boot from the CD you must set your computer's BIOS to boot from the CDROM drive. Consult your motherboard (or computers) manual or google it if you don't know how to access the BIOS. You can't just stick the CD in a running Windows system and expect it to launch by itself.
Here is a great site for getting started with Ubuntu. Read through all of the topics on the left side of the page:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by delpgdn on 2009-03-04
thank you for help problem solved  now back to ati headache

---

### Post by tommcd on 2009-03-05
> **delpgdn said:**
> thank you for help problem solved  now back to ati headache

Glad you got Ubuntu installed! Welcome to the cool side of computing!
If you are having trouble with ATI drivers, then perhaps start a new thread on that. Or try searching om google or these forums. There is a ton of information here.

Just to let you know...
Please try to describe your problem by providing **as much information as possible** when you post here. You can't just just give a half sentence blurb and expect people to be able to understand what is going on and help you solve your problem. Don't be shy. Tell us what is going on in complete detail, including any errors you may get.

Have you tried going to: [system > administration > hardware drivers] to see if you can enable your ATI driver with a single click? And please read all (and I do mean *all*) of that psychocats website I gave in my last post. There is a learning curve to using linux. You will have to do some reading to get the most out of it. How much you understand about your new linux system is entirely up to you.

---

