---
title: "Intuos 4 (large usb) configuration on Oneiric - Ubuntu 11.10"
date: 2011-10-27
forum: Hardware
---

### Post by mike2046 on 2011-10-27
Hi,

I've upgraded to Ubuntu ** Oneiric **and I'm trying to set the buttons on the Intuos4 pad. Following the advice on the posting re the Bamboo tablet I have updated to the latest driver via git. I have confirmed that the tablet buttons are assigned to buttons 1,2,3,8,9,10,11,12 and 13, and been able to assign keys to each of these buttons. However,  I am having a problem with assigning the alt key to a button. For example, when I try to do the following

xsetwacom set "Wacom Intuos4 8x13 pad" Button 3 "key alt"

it doesn't work, whereas for example

xsetwacom set "Wacom Intuos4 8x13 pad" Button 3 "key x"

does work. Basically any key assigments I try involving the alt key are not working.

Any advice on what I need to do to correct this would be appreciated. Also how would I go about setting the LEDs on the tablet?

Thank you

Mike2046

---

### Post by Favux on 2011-10-28
Hi mike2046,

Welcome to the Ubuntu forums!

According to the xsetwacom.c code that should work:
```
	{"alt", "Alt_L"},
	{"lalt", "Alt_L"},
	{"ralt", "Alt_R"},
```
You could try "Alt_R" etc. or add the press +alt I suppose.

LED and OLED support were just added to the 3.2 kernel so Oneiric's 3.0 doesn't have it unless you patch.  However a backport version was added to input-wacom.  Not sure how much you lose with that version.  Eduard is adding the X driver side of the OLED support to xsetwacom currently (haven't heard anything for a week or so), see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up)  The Intuos4 OLED thread has folks already using the patches.

---

### Post by mike2046 on 2011-10-29
Hi Favux,

Thanks for your reply. I have tried each of the suggested options, and +Alt as well. In each case all I get when I press the button on the tablet is a dash.

Everything is working great apart from this. I suppose getting the buttons working on my Inutuos4 is "the icing on the cake". Do I need to update my version of xsetwacom?

---

### Post by mike2046 on 2011-10-29
Hi Favux,

Given your comments about the source file saying it should work, I've now downloaded the xf86-input-wacom-0.11.1.tar.bz2 and run ./configure and make on this. When I try using this version of xsetwacom the alt key works as expected. 

I had previously followed the instructions you gave in Appendix 2 of the thread 

 [B]HOW TO Set Up the Bamboo Pen & Touch in Lucid 

[/B]to update my wacom.ko file. I didn't realized that I needed to update xsetwacom as well. That thread was also very helpful in explaining how the button assignments had changed.

Thanks very much for your help, and for all the work of the Wacom Linux team which makes all this possible.

---

