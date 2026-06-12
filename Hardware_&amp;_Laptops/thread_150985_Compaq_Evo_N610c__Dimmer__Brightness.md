---
title: "Compaq Evo N610c : Dimmer / Brightness"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by quail-linux on 2006-03-27
Hi All,

I am having problem with my laptop with the Dimmer / Brightness as they don't work.  I have be searching high and low to fix the problem but just keep hitting ](*,) hehe. I am running Breezy.

TiA

Dale

---

### Post by dresnu on 2006-11-01
This post is very old :-D. I just wanted to state my experience though.
I have found out to my big delight that brightness control works perfectly for this laptop on Edgy. You can change it by pressing Fn+F10+Up/Down Arrow to increase or decrease it respectively.

---

### Post by quail-linux on 2006-11-02
> **dresnu said:**
> This post is very old :-D. I just wanted to state my experience though.
I have found out to my big delight that brightness control works perfectly for this laptop on Edgy. You can change it by pressing Fn+F10+Up/Down Arrow to increase or decrease it respectively.

Hi,

Thanks for the info, but my N610c died. But it great to hear that brightness control is working correctly now :-)

Regards
Dale

---

### Post by Eddie Hung on 2007-01-10
> **dresnu said:**
> This post is very old :-D. I just wanted to state my experience though.
I have found out to my big delight that brightness control works perfectly for this laptop on Edgy. You can change it by pressing Fn+F10+Up/Down Arrow to increase or decrease it respectively.

Wow what a find! I can confirm that this works on my n410c too!

The only slightly scary thing is that my screen is now very very bright... much brighter than what I can set with the compaq (windows) software... oh well!

Maybe a suggestion would be to have some sort of visual feedback as to Fn+F10 was indeed recognised, and feedback as you're adjusting it!

Next step - getting gnome-power-manager to work with it!

Eddie

EDIT: This is tested under latest feisty, but as the poster above me says, it seemed to work in edgy!

EDIT2: Just found out that this trick works during boot up, which means that it's not driver operated - but instead is part of the BIOS of something very low level like that - meaning that it's not so much that edgy/feisty implemented some code specifically to adjust brightness, but instead just simply allowed the keys to be passed through to the BIOS...?

---

### Post by lawentzel on 2007-03-19
I have a Compaq Prosignia, and the Fn + F10 plus arrows works for me as well. :)

---

### Post by Jonathan Métillon on 2007-03-28
> **dresnu said:**
> You can change it by pressing Fn+F10+Up/Down Arrow to increase or decrease it respectively.

Life saver! I was thinking that my Compaq N610c's LCD panel was dying ;-)

Thank you!

---

### Post by breals on 2007-04-06
Darn. This doesn't work for me on the N610c I'm building for a friend who's never owned a personal computer.  Anyone know of a way thru bios to change the brightness?

Hmm...I wonder if I upgraded to Fiety if this would get fixed.

Bill
[http://www.reals.net](http://www.reals.net)

---

### Post by Eddie Hung on 2007-04-06
> **breals said:**
> Darn. This doesn't work for me on the N610c I'm building for a friend who's never owned a personal computer.  Anyone know of a way thru bios to change the brightness?

Hmm...I wonder if I upgraded to Fiety if this would get fixed.

Bill
[http://www.reals.net](http://www.reals.net)

I believe this key is implemented in hardware (i.e. BIOS) rather than software (the operating system).

Have you tried pressing Fn+F10, and then pressing the up key and down keys. Each up and down keypress for the next few seconds changes the brightness - but you don't get any feedback as you do when you have the compaq software installed in windows.

Try that?

Eddie

---

### Post by breals on 2007-04-07
> **Eddie Hung said:**
> I believe this key is implemented in hardware (i.e. BIOS) rather than software (the operating system).

Have you tried pressing Fn+F10, and then pressing the up key and down keys. Each up and down keypress for the next few seconds changes the brightness - but you don't get any feedback as you do when you have the compaq software installed in windows.

Try that?

Eddie

Here are the details on the laptop which is an Easter present for a friend:
[LIST]
[*]I'm running a Compaq Evo N610c
[*]The compaq has a an ATI graphics card
[*]I've got Ubuntu 6.10 Edgy running
[/LIST]

Here is what I've tried so far:
[LIST]
[*]i've tried chording fn+f10+arrow keys but it doesn't do anything.
[*]I've tried running xev and seeing if I can get the FN key to register as an event,  but it doesn't register any event for the fn key,  kinda like the key doesn't exist to the computer. Other keys do register events in xev
[*]I've tried searching for function keys, fn keys, and even gone into the bios to see if you can adjust the bios but I can't find anything.
[*]I've found a way to adjust the gamma but that only helps the contrast, not the overall brightness of the screen which it desperately needs.
[/LIST]

It looks like I might want to try Feisty.

---

### Post by Eddie Hung on 2007-04-07
> **breals said:**
> Here are the details on the laptop which is an Easter present for a friend:
[LIST]
[*]I'm running a Compaq Evo N610c
[*]The compaq has a an ATI graphics card
[*]I've got Ubuntu 6.10 Edgy running
[/LIST]

Here is what I've tried so far:
[LIST]
[*]i've tried chording fn+f10+arrow keys but it doesn't do anything.
[*]I've tried running xev and seeing if I can get the FN key to register as an event,  but it doesn't register any event for the fn key,  kinda like the key doesn't exist to the computer. Other keys do register events in xev
[*]I've tried searching for function keys, fn keys, and even gone into the bios to see if you can adjust the bios but I can't find anything.
[*]I've found a way to adjust the gamma but that only helps the contrast, not the overall brightness of the screen which it desperately needs.
[/LIST]

It looks like I might want to try Feisty.

That's what I mean - the OS does not see these Fn+ anything keys - just like the numpad keys (accessed by Fn+key) generate the native key.

Silly question - but does it/has it ever worked in Windows? I ask this because one reason could be your LCD panel is simply broke.

Because if I remember correctly (will test again when I next reboot), that key press even works when in GRUB for me, as it is implemented in hardware.

EDIT: I use a Compaq n410c - but I believe it is identical to the n610c, just that you have a bigger screen?

Eddie

---

### Post by breals on 2007-04-07
> **Eddie Hung said:**
> 

Silly question - but does it/has it ever worked in Windows? I ask this because one reason could be your LCD panel is simply broke.

Eddie

 yes, the fn key worked in Windows and it's the only key that isn't working now. I'm upgrading to Feisty right now to see if it solves the problem.

---

### Post by breals on 2007-04-07
Well Feisty fixed it kinda of.

I can now use the fn + F10+ arrows during the boot up, so I just cranked up the brightness then and it's brighter.

Feisty seems a little bit slower on boot up but the network manager enhancements are much better.

---

### Post by oldtappan on 2007-05-20
On my Evo 610c, the Fn+F10 + up/down only worked when I went into the BIOS.  It didn't work for me when I was logged onto my desktop.

---

### Post by kaosteori on 2007-05-29
Hello all,
I just changed the memory of this laptop which died now i have a kingston 512 Mo and i'm a new linux user i just installed edgy eft I'm looking also for installing Feitsy but i must solve two problems before .
First : which driver should i install to have my CG ( Ati M7 LW  or mobility radeon 7500 ) and if it's possile can give me a complete how-to.
And i have also another problem with my network i loose the connection 4 min after the boot i tried with 2 different routers an Peabird and a d-link G624T can you help me plese if you need some logs or results of command no problem.
Thanks

---

### Post by dresnu on 2007-05-30
About the first issue can you post the output to this command: ```
cat /etc/X11/xorg.conf
```

---

### Post by kaosteori on 2007-05-30
Now i'm having some exams . so i'll post the output when i can because i must boot on edgy save the output as a .txt file and bachup it in a USB key and ater tha reboot to win and finally post it .
Thanks a lot for your help .
PS: don't care if there is some mistakes i just speak english a little .

---

### Post by naraic on 2007-06-10
I've got the Compaq N610c also, but the button combinations mentioned above won't work for me running Feisty.  They do work during Bios though....  If I could get this working, i will have no issues left at all.  It's not really even that big a deal, unless it's not plugged in.
Also, has anyone else been having trouble with the laptop getting extremely hot?

Thanks

naraic

---

### Post by dresnu on 2007-06-10
I no longer have an evo and I only reached edgy upgrade with it so I can't help you with the feisty problem, though I remember clearly that one of the main reasons I switched to another laptop was exactly because it was going extremely hot after just e few minutes of work.
I think that the components on that system are positioned in a bad way not helping the (small) fan to disepate the heat.
Your laptop might also have collected a lot of dirt and dust inside over time.

The best solution to this problem, even though it doesn't help that much, might be to open the case and clean up the whole thing with a vacuum (carefully!). You might also consider changing the thermal paste of the cpu, though most of the heat generates from the hard disk.

---

### Post by belias on 2007-09-10
OMG i was at the carwash and remembered the advice above, so i used the vacuum there to clean the inside and many of the inner components got sucked in. What can i do?? 

On a side note, my evo610c also ran very hot before it got sucked away.

---

### Post by nogasbiker on 2007-10-16
I've been running SLED10 for awhile, and the F-10 worked fine for setting brightness.

I now moved to Feisty Fawn, and notice the F-10 no longer worked.  It does work briefly, but once the dialog box for password shows up, F-10 has no effect.

Is X on Feisty doing something usual with the keyboard?

---

### Post by CrunchyFrog on 2007-11-03
I have recently bought a 2nd hand Compaq EVO n610c and with Ubuntu 7.4 installed couldn´t get the FN / F10 key combination for brighness control to work too.
Astonishingly to me the keys worked when using the live-CD (pre release) of that same distribution.
I was going to post that and to hope some tech guru could look into the difference beween the two versions.
But this may be not necessary anymore, because since I have upgraded to 7.10 yesterday the FN/F10 key combination works for brightness control. (press FN and F10 simuntaneously and afterwards arrow up or down for adjusting the brightness)

So, good news to all EVO 610 users (and some similar notebooks I guess).

---

### Post by nogasbiker on 2007-11-26
I just did a fresh install of 7.10 gutsy gibbon.  The brightness problem on the Evo n610c does in fact go away.  Thanks

[ New problem though, the fan seems to be stuck on low all the time.  There have been other reports of this for Gutsy (on different model laptops).  It is blowing cold air so it isn't necessary to run the fan.  There is a bad effect because of the annoying noise and reduced battery life. ]

---

