---
title: "Lenovo T61 mem resource failure"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by mog27 on 2007-10-23
I have a Lenovo Thinkpad T61 and everytime I boot up into Gusty Gibbon, the following message quickly flashes:
[    1.348000] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0

Anyone familiar with that?  It doesn't affect anything; It still boots.  But how do I get rid of it?

---

### Post by knightzor on 2007-10-23
I have the exact same message on my T61. Like you said, I don't think its affecting anything but would be interesting to know why it is doing it/how to resolve it.

---

### Post by mog27 on 2007-10-25
No ideas?

---

### Post by alexsb on 2007-10-25
Same problem here on my T61, no obvious effects, no ideas for a solution.

---

### Post by Calyce on 2007-10-25
I have the same problem on a R61 (8918-5QG). As previously said, no obvious effect. This problem can also be observed with Ubuntu 64 bit. I don't have a clue of what it is

---

### Post by brenix on 2007-10-31
Im getting the same message on a T61p. It does not seem to cause any issues or performance changes. Though I had assumed it might be my 1GB Intel Turbomemory..

---

### Post by rybu on 2007-10-31
I have no idea if I'm getting that message.  When I boot up, I get a blank screen until the log-in screen appears. 

Well, usplash comes up and grub lets me choose a kernel.  But the Ubuntu splash screen (where you get system notifications that you're talking about) does not appear at all.  It's been like this since the 7.10 RC came out.  I never had this problem with any of the alpha or beta distros for 7.10.

---

### Post by mrpeanut on 2007-10-31
I have nothing to contribute other than that I also get the message.  Unlike brenix I don't have Intel Turbo Memory, so I don't think it's related to that.

---

### Post by mkurtgis on 2007-11-07
I also have this message but I am not running ubuntu I am running Fedora.  Originally I did not see this message when I installed Fedora 7 but when I recompiled the kernel to 2.6.23.1 it showed up.  When I go back to the the fedora 7 kernel it goes away.  I tried copying the .config file from the fedora 7 kernel source and recompiled the new kernel with that but it didn't work.  Not sure what it is but thought the extra info would help.  If I figure out what it is I will let you guys know

---

### Post by Ansible on 2007-11-11
I get the message too; t61p booting the ubuntu 7.10 dvd.

Whats interesting is I also get the message on a quad xeon box with an 8800 gts video card.  No idea what it means, it doesn't seem to affect my xeon install.

---

### Post by KC9EVP on 2007-11-13
Just bought a T61 too. Same error but since its not affecting the performance I will ignore it. Perhaps 8.04 or a system update will fix it.

---

### Post by syxbit on 2007-11-17
this is fixed by kernel 2.6.24
so it will be fixed in Hardy in April

---

### Post by emptythevoid on 2008-01-07
I'm replying to the specific problem of no "loading" screen when booting 7.10.  I don' t know what causes this problem, but I've experienced it on three computers that didn't have a problem on Feisty.  Here's how I remedied it:

1.)  Go to Synaptic, search for startupmanager, and install it.
2.)  Run the program (you'll find it in System->Administration->StartUp-Manager
3.)  Make sure "Show Boot Splash" is checked.  If it's already checked, uncheck it and recheck it.  (actually, here's what I did:   I unchecked it and hit close.  Then I opened the manager back up and re-checked it and hit close)
4.)  Hit close and reboot.  

That should clear up the black screen during loading for 7.10.

---

### Post by jviegas on 2008-01-23
I also have a similar problem, in my clevo d900k

   I get the following message:

Starting up ...
[      0.696000] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:0
2:00.0
Loading, please wait...
_

   Then Ubuntu starts loading normally but my usb mouse is not working and my wacom works only as mouse mode. Could it be this error?
   In version 7.06 I did not get any of these but I had no graph card driver support. 
Is it possible that if  I reinstall the 7.06 version and do the updates I can get the problem fixed?

Best
Joao

---

### Post by Ansible on 2008-03-28
Can anyone testify that this is indeed solved in 8.04?

---

### Post by Bobbafett on 2008-03-29
Hello,
I also have a problem with my T61 :(
When trying to boot up from the Live CD I see this message popping up just before the "Loading" Ubuntu screen comes up, then the screen goes dark.... apparently never gets to load Ubuntu or have a problem with the video, the fact is that NOTHING ever shows up :(

---

### Post by hvac3901 on 2008-03-29
T61 here, talking to you form it now. I have never received this message EVER. only thing that happens to me is the network manager hangs up bad from time to time. ELSE all is golden.

---

