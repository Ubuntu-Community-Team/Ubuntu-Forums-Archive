---
title: "how to disable laptop keyboard?"
date: 2010-06-11
forum: Hardware
---

### Post by sandy8925 on 2010-06-11
I need to disable my laptop's inbuilt keyboard due to some problems i'm having. the w key keeps getting typed on screen. I'll be using an external keyboard connected through usb. 

i'm using kubuntu 10.04 on a sony cr35g. can someone please tell me how to do this? (disabling the inbuilt keyboard that is).

i would prefer a graphical method because of the keyboard problem but commandline should be ok too if i can execute the commands in a script.

---

### Post by pricetech on 2010-06-11
Am I reading that correctly that the W key is spontaneously registering a key press without actually being pressed ??

I doubt there's any way to disable it outside the BIOS, and maybe not even there.

I'd look at removing the keyboard and attempting to fix whatever is going on with the W key and if worse comes to worse, leaving it disconnected.

---

### Post by yossell on 2010-06-11
This doesn't seem to be what you asked for, but if it's just the w key giving you problems, you could disable it and remap your keyboard so that another key or key combination gives you w.

I've never done it myself so can't verify that it works but

[http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/](http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/)

gives some instructions on how to do this - maybe it allow you to use your original keyboard.

---

### Post by sandy8925 on 2010-06-12
@pricetech - yes that's right. that's bad - like all laptops the bios has been dumbed down and obviously none of the advanced features are available.yeah it is a keyboard problem since it also happened in vista which was previously installed.

@yossell-  thanks for the info.will check it out.

---

### Post by sandy8925 on 2010-06-12
@singam - Urm this is ubuntuforums.org and i'm talking about kubuntu. windows has been eradicated from my laptop!

---

### Post by sandy8925 on 2010-06-13
@yossell - I used the command given in the link and it worked! My laptop's inbuilt keyboard w key does not work when pressed (and more importantly does not spontaneously register a press) but my external keyboard's w key works fine. So do I have to this each time the comp is started or is it sort of permanent?

---

### Post by yossell on 2010-06-13
Hey - I'm glad it worked, though I'm surprised that it worked that well - I thought it was going to disable the w button on each keyboard. 

I don't really know the answer to your question, but a quick look around does suggest it's possible to apply these remaps automatically on start up - these links looked like they might be helpful:

[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

[http://dev-loki.blogspot.com/2006/04/mapping-unsupported-keys-with-xmodmap.html](http://dev-loki.blogspot.com/2006/04/mapping-unsupported-keys-with-xmodmap.html)

---

### Post by sandy8925 on 2010-06-14
well actually i executed the command before conencting the external keyboard. which is probably why the external keyboard's w key is working and the inbuilt keyboard isn't.

---

### Post by sandy8925 on 2010-06-17
my problem isn't solved yet. unfortunately it STILL occurs even after disabling the  key using: xmodmap -e 'keycode 25='

anyway to disable the internal keyboard? change something in xorg.conf?

---

### Post by sandy8925 on 2010-06-21
ok the problem doesn't occur anymore atleast when using a window manager or desktop environment. i've set the command to run each time i start up the laptop. unfortunately the command cannot run before loading kde, so the problem still occurs during login.

---

### Post by thorsten muller on 2010-09-23
for me the following worked:

edit /etc/default/grub
you must edit in superuser mode

change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nokbd"

some sources say it should be i8042.nokbd=1 but i8042.nokbd worked for me

after that run
sudo update-grub
to get the changes into /boot/grub/grub.cfg

---

### Post by nerdse on 2011-09-19
> **thorsten muller said:**
> for me the following worked:

edit /etc/default/grub
you must edit in superuser mode

change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nokbd"

some sources say it should be i8042.nokbd=1 but i8042.nokbd worked for me

after that run
sudo update-grub
to get the changes into /boot/grub/grub.cfg

Question: Does this not work in regular Ubuntu? I am not good with the command line, so have to ask also, is there something I put in front of the "edit/etc/default/grub" part? When I tried that line, I got a message saying there was no such command. I'm using 11.04 but without the Unity interface because my laptop is too old to use Unity. I tried also typing in the line "GRUB_CMDLINE_LINU_DEFAULT="quietsplash"" but again, got the message no such line exists.

If this is for Kubuntu, & that is the problem, apparently there is no common use as I was led to believe, so, does anyone know if this can be done in Ubuntu & how? My keyboard just started to stick. Compressed air, little skinny ribbons of cotton with isopropyl alcohol, gently using a mechanical pencil tip sans the lead to push things out from under, are useless & if anything, have made the keyboard worse. Using a USB is difficult as even when they are separated by a couple feet, they interfere with one another. I'm not well; digging into the laptop & taking it apart, esp. with my on again-off again eyesight, is really not feasible...I would think disabling a keyboard in BIOS might also disable a USB keyboard.

Anyone out there got any practical help for me? I rely on the computer to try & keep up with continuing education online in hopes of someday being well enough to return to work...not being able to type without pounding the keyboard until my fingers are in agony, having letters miss or repeat, having the space bar not function, pounding the same key repeatedly to get it to work, are all intolerable.

---

### Post by Olivia Wagner on 2011-09-19
I know that keyboard not working properly leads to a terrible situation. I'm also not very used to mouse and completely depend on keyboard shortcuts. And I think whether you try a million times, keyboard cannot be repaired completely. Once a problem come, you need to replace it by a new one. But if anybody here can give a complete solution to this, then I would be thankful.

---

