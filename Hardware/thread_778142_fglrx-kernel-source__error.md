---
title: "fglrx-kernel-source_ error"
date: 2008-05-01
forum: Hardware
---

### Post by johnswb on 2008-05-01
I've looked and looked for a HowTo: Install Ubuntu 8.04 with an ATi x1600 video card and have had no luck.  I can't believe that I'm the only one with this problem?  Everything I can find only talks about 7.10.  My guess is I need to stick with 7.10 until 8.04 can run ATi cards.  
 
Please; if anyone can give me a site or how to get the fglrx-kernel-source_8.42.3-1_i386.deb installed would be great.  I will keep looking maybe I'm just over looking it.... grrrr

---

### Post by Shockwav on 2008-05-02
x1600 here too. I did an upgrade without checking first. :frown:

Compiz - gone; too slow
3d Games - gone; jump and lag.
Screensavers - gone; 1,1.5 minutes to get my machine to wake up.

The standard free drivers run like a one-legged jackrabbit.

I'm stuck until someone can give up a fix for this.

In the meantime if you can go back to gutsy without too much heartache, I would recommend it. Just don't give up on it.

---

### Post by johnswb on 2008-05-04
I got the ATI driver working with fglrx in Ubuntu 8.04. 

Here is what I did.  Hope this works for you.

Note: You will need to reboot if you don't on step 6. I only reinstalled because I wanted to make sure I didn't have anything extra stuff I forgot about, and to make it easy to doc for anyone else that is having the same problem.  In Ubuntu 7.10 I had to do more to get it working and now in 8.04 it takes less.  I was making it hard....

1. Reinstalled... 

2. Logged in after installation enabled the ATi accelerated graphics driver

3. Downloaded the ATi driver from [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run").

4. sudo chmod +x ati-driver-installer-8-4-x86.x86_64.run

5. sudo ./ati-driver-installer-8-4-x86.x86_64.run and go with defaults 

6. Reboot - this is optional, I did reboot here fyi

7. Click "System" - "Appearance" - "Visual Effects" - "ExTra" then close

8. sudo apt-get install compizconfig-settings-manager

9. Enjoy

I like to thank the Ubuntu Team for all the hard work they have done.

---

### Post by Shockwav on 2008-05-05
I got mine working!!! 
Sucks that I had to use EnvyNG to do it but I'm back!

---

### Post by morphx on 2008-05-07
Unfortunately it didn't work for me -- XOrg is still using the OpenSource drivers and I still need to "sudo aticonfig --initial -f" every time I log off or reboot

---

