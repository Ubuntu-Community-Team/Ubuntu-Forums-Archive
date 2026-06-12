---
title: "Novatech N3 Laptop problems"
date: 2011-06-02
forum: Hardware
---

### Post by dwfait on 2011-06-02
Hi all. I've just purchased Novatech N3 laptop and couldn't get Ubuntu to install. I tried from USB stick, DVD disc, both 64 and 32 bit versions, but the result was the same - after the initial Ubuntu screen with the keyboard = human logo, it was a blank screen and nothing happened.

I've installed Debian on there fine, however. But I would like to get Ubuntu on there as I need it for my final year project.

Does anyone have any suggestions as to why Ubuntu wouldn't install and Debian would? Can anyone recommend an alternate installer for it, or perhaps a way to install it from within Debian?

---

### Post by manfromthezoo on 2011-06-02
dwfait, what version(s) of Ubuntu are you trying to install?

---

### Post by dwfait on 2011-06-02
Oh sorry, forgot to mention that - 11.04, normal edition (not server). I believe the netbook edition and desktop have merged into one with 11.04, yes?

---

### Post by manfromthezoo on 2011-06-02
That's right, there's harmonisation now to 'just' Ubuntu rather than separate editions. That's a benefit from Unity adoption.

Out of interest, it would be interesting to see if you were able to boot from a 10.04.2 CD or USB stick - that way, we could start narrowing down whether the problem is with the 11.04 installer and your hardware / hardware config or something more 'show-stopping' altogether.

---

### Post by candtalan on 2011-06-02
(thinking aloud here)
consider using  

nomodeset

when initially booting from the cd usb whatever. One of the F key options includes an option, but I usually actually edit the boot string (press 'e' I think after getting the initial boot menu after a key press after seeing symbols keyboard=human)

(Where are you located, I am in bracknell?)

---

### Post by dwfait on 2011-06-02
I just downloaded and burnt the 10.04.2 LTS version, and it's installing fine. Huh. I'd have expected the 11.04 version to have BETTER hardware support.

---

### Post by candtalan on 2011-06-02
I am close to a Novatech outlet and I am also on their forums. And I have spoken to the manager at my local store, and unfortunately they are not unduly  interested in gathering information about Ubuntu compatibility, very few of their staff use anything other than Windows it seems. I did extract a very special concession that in the occasion I wanted to make a purchase, by prior arrangement with him, it would be possible for me to test a machine (with Ubuntu)  in store, likely with a chaperone at my shoulder (this is retail wild west of course).

The problem  you find with 11.04 may not really be with Ubuntu, I think it is just difficult for devs to keep up with whatever hardware (Novatech) happen to throw into their machines one day.

You personally can be a very significant help in this situation by gathering suitable information about your N3. 

The best way to support this situation I believe is to go to the trouble of registering a bug for 11.04, I would certainly encourage you to do that. Goes without saying that others will also be keen to learn from your N3 if you have time.

best wishes

---

### Post by dwfait on 2011-06-02
> **candtalan said:**
> I am close to a Novatech outlet and I am also on their forums. And I have spoken to the manager at my local store, and unfortunately they are not unduly  interested in gathering information about Ubuntu compatibility, very few of their staff use anything other than Windows it seems. I did extract a very special concession that in the occasion I wanted to make a purchase, by prior arrangement with him, it would be possible for me to test a machine (with Ubuntu)  in store, likely with a chaperone at my shoulder (this is retail wild west of course).

The problem  you find with 11.04 may not really be with Ubuntu, I think it is just difficult for devs to keep up with whatever hardware (Novatech) happen to throw into their machines one day.

You personally can be a very significant help in this situation by gathering suitable information about your N3. 

The best way to support this situation I believe is to go to the trouble of registering a bug for 11.04, I would certainly encourage you to do that. Goes without saying that others will also be keen to learn from your N3 if you have time.

best wishes


I certainly do have time, and would love to help the Linux community as I can :)

Just a quick update though - 10.04.2 has installed and everything seems to work out of the box, including Wireless which was having problems in Debian.

I'm based in Portsmouth by the way, very close to Novatech's headquarters and have been going there for years. I know their official policy is that they don't support or recommend Linux, which I do think is a bit silly given that their customer base is usually a bit more technically oriented than the folk who usually shop at PC world.

I'm not all THAT familiar with Linux though, so I may need a bit of help gathering all the information I can. I can certainly put in a bug report though.

---

### Post by manfromthezoo on 2011-06-02
Fareham based here :D

Yes, unfortunately I've always had the same response from Novatech too, regarding Linux. They're slowly, slowly getting better at accepting its existence, but it can still be a bit of a struggle with their support guys.

A friend of mine who worked there once told me the laptops were primarily manufactured by Mitac or Uniwill - but I'm not sure if that still stands, it may be old info by now.

Still, you need to give them props for allowing you to buy the machine without an OS, and no imposed Windows tax.

dwfait - I'm not sure how much time you have on your hands, or if you're willing to go through two upgrades, but you could always do an in-place upgrade to 10.10, then onto 11.04 from there. Think of it as connecting flights ;)

Press ALT+F2, and then at the prompt, type:

update-manager -d

It should launch Update Manager with the option to upgrade to 10.10. Do this after you've applied all existing patches for your 10.04.2 installation. Then, repeat and rinse once 10.10 is installed; make sure you're patched up-to-date, then repeat the commands above. You should be offered the upgrade to 11.04

Long-winded, I know, but it may get you using 11.04 quicker.

---

### Post by candtalan on 2011-06-02
>  . . . . . You should be offered the upgrade to 11.04 .....
Long-winded, I know, but it may get you using 11.04 quicker.

How do you know that 11.04 will work better when installed and not just have the graphics or whatever just fall over? I suppose the worst that might happen might be a reinstall of the earlier version again. 
If it is the nomodeset thing, then  this can be tested at live CD stage to add some certainty I think. Although unity will probably not be available.

---

### Post by candtalan on 2011-06-02
> **dwfait said:**
>  ... I'm not all THAT familiar with Linux though, so I may need a bit of help gathering all the information I can. I can certainly put in a bug report though.

Well done you! I am no expert at all and have to struggle to register bugs, but a recent one I did (as a newbie) with a 11.04 prob is here and you might find it useful as some sort of example, it seemed to get understood but it felt I was pretty clumsy with it
=======================
Example only:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/762135](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/762135)
=======================

Re possible bug report:
you can gather a lot of information about the machine now that your 10.04.2 + updtaes is installed, the machine and chips etc will not change. You can test compiz graphics (used in 11.04) easily in 10.04 also - you get the idea? 

More power to your elbow!

---

### Post by manfromthezoo on 2011-06-03
> **candtalan said:**
> How do you know that 11.04 will work better when installed and not just have the graphics or whatever just fall over? I suppose the worst that might happen might be a reinstall of the earlier version again. 
If it is the nomodeset thing, then  this can be tested at live CD stage to add some certainty I think. Although unity will probably not be available.

I don't know that 11.04 will work better; you may be bang on and **nomodeset** may do the trick. It's a good suggestion. But since we don't *really* know what's causing the hang for *sure*, there's nothing to say it's going to fail because of a graphics issue (as we don't know the cause). Both worth trying, for certain.

Just a thought / an additional route dwfait can take if curious.

---

