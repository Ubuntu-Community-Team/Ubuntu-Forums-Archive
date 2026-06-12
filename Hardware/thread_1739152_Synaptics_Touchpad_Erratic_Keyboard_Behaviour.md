---
title: "Synaptics Touchpad Erratic Keyboard Behaviour"
date: 2011-04-25
forum: Hardware
---

### Post by NBFruit on 2011-04-25
I have a HP Probook 4520s, which has a Synaptics Touchpad.

I am running Lucid Lynx 10.04

Linux rosco 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux

The Touchpad works fine when booted into Windows 7, but when I use it in Ubuntu, it produces very erratic keyboard behaviour. For instance, I could be typing in a textarea in a web form, and suddenly the cursor will jump and to a different part of the text I have justed typed.

The only solution is to disable the Touchpad and use a mouse, which really isn't ideal. Also, the touchpad sometimes 'magically' re-enables itself without my intervention.

I've installed the Linux driver supplied by HP, but this didn't make any difference.

Has anyone else experienced this? Its extremely annoying. I use my laptops on planes and trains all the time, and having to use a mouse is a real pain.

G

---

### Post by mörgæs on 2011-04-26
Does this help?
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by NBFruit on 2011-04-27
> **mörgæs said:**
> Does this help?
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

No

---

### Post by mörgæs on 2011-04-28
If you want help, you must provide us with a little more than 'no'. 

Please give a thorough description of what you have tried and the results. First of all you should test 10.10 and 11.04.

---

### Post by NBFruit on 2011-04-28
> **mörgæs said:**
> If you want help, you must provide us with a little more than 'no'. 

Please give a thorough description of what you have tried and the results. First of all you should test 10.10 and 11.04.

The link you posted merely details how to configure a Synaptics Touchpad.

I don't have any issues configuring it. The touchpad works. The problem is that when it is on, the keyboard doesn't work as expected.

What I have tried:

Installed the Synaptics Driver directly from HP.
Installed gsynaptics

I will probably upgrade the kernel over the coming weeks, but I'd prefer to get to the bottom of this.

---

### Post by NBFruit on 2011-05-05
Have tried a few more things. eg Touchsave.

Behaviour is the same regardless.

Touchpad remains on while typing, no matter how I configure it, and cursor still jumps around the screen.

For instance, I could be typing an email message, and suddenly my cursor will jump into the subject field of the email messages.

I have my doubts whether a kernel upgrade will fix this, but I am going to try tonight.

Synaptics Touchpad is piece of junk. I'd avoid any laptop that uses it.

---

### Post by NBFruit on 2011-05-07
> **NBFruit said:**
> I have my doubts whether a kernel upgrade will fix this, but I am going to try tonight.


Upgraded to 10.10. No change.

Well, there is a change. The Touchpad has now stopped working, in that right click is no longer available.

---

### Post by mörgæs on 2011-05-07
Have you tried a clean install of 11.04?

---

### Post by carld on 2011-05-13
Experiencing same issue as NBFruit on an HP probook 4320s, using 11.04. I set the touchpad disabled while typing in the GUI, but that doesn't work as it's intended --- while typing my hand/palm over the touchpad causes the cursor to move. Any other suggestions to disable touchpad while typing? Thanks

---

### Post by carld on 2011-05-14
So far what might work for me is to follow instructions found in this link and using syndaemon -i 1.5 -t -k -d 
[http://ubuntuwiki.net/index.php/Touchpad,_disabling_while_typing](http://ubuntuwiki.net/index.php/Touchpad,_disabling_while_typing)

---

### Post by NBFruit on 2011-05-24
I've determined that this  is actually a problem with the palm of my hand glancing off the touchpad when typing. When this happens, the cursor jumps to whereever the mouse is pointing on the screen.

If the mouse if pointing at a menu option, this drops the menu, and further keyboard strokes then select menu options. This can have disasterous results when typing texts (think Select All).

Gsynaptics is supposed to include palm detection, but neither this nor the 'Disable Touchpad While Typing' options work in Ubuntu.

My solution?

I went to my hardware store and bought a strip of draft excluder tape. I stuck 2 strips down each side of the touchpad, which prevents my palm from glancing off the surface.

It distorts my typing flow a little, but I'm hoping that I can adapt to that.

I really blame Synaptics for this, and HP, for poor design.

I will never buy another laptop that doesn't have a recessed touchpad.

---

### Post by mörgæs on 2011-05-24
Well, I didn't think of that... :-)

Good that you got it solved. Please mark the thread so.

---

### Post by NBFruit on 2011-05-24
> **mörgæs said:**
> Well, I didn't think of that... :-)

Good that you got it solved. Please mark the thread so.

Actually, I just tried the syndaemon solution posted by carld too.

I'll let that run for a few days first and then post SOLVED.

---

