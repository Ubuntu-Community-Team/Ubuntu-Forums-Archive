---
title: "Dell Inspison 6000 - Screen not turning on after closing lid"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by ninocass on 2005-12-12
Hi

when i close the lid on my laptop and open it again the screen stays blank but i am able to toggle caps/num etc so the computer is responding.  This only happened recently and i cant think of what ive changed that would be causing this.  I have checked the power options and the laptop is set to do nothing when the lid is closed

thanks

Nino

---

### Post by ninocass on 2005-12-12
it seems that if i close the lid and come back maybe 30 minutes later it works but if i leave it ~15  theres no change :(

---

### Post by ninocass on 2005-12-12
ive done a search and it seems the common problem is the computer going into stangby, to test this i closed the screen and conntected via VNC.  i also removed everything in lid.sh and commented out lidbtn so nothing should happen when i close the lid but alas the screen stays blank

i looked in the acpid log files and this is what happens when the lid is closed:

```

[Tue Dec 13 01:33:45 2005] received event "button/lid LID 00000080 00000005"
[Tue Dec 13 01:33:45 2005] notifying client 7041[111:111]
[Tue Dec 13 01:33:45 2005] completed event "button/lid LID 00000080 00000005"

```

im now getting:

```

root@Laptop:/etc/acpi# ./lid.sh
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xset:  unable to open display ":0"
root@Laptop:/etc/acpi#

```

when i try and run ./lid.sh

im running out ideas :(

Nino

---

### Post by ewinslow on 2005-12-12
That's interesting that you actually had suspend working before. It never worked out of the box for me. I have to use hibernate only. I'm assuming you have the ATI video card.

Here's a thread that focuses on the ATI card. There are some posts specific to the Inspiron 6000 in there, too. You might find something in there helpful. I've tried the tip in there (as you'll see), but suspend is still way flaky. Seems like there is a 50/50 chance of it actually working right. I think I'm just going to wait for Dapper Drake to come out.

[http://ubuntuforums.org/showthread.php?t=83201](http://ubuntuforums.org/showthread.php?t=83201)

---

### Post by ninocass on 2005-12-13
hi

i eneded up formatting and reinstalling Ubuntu and its working ok now, tis strange.

i have the onboard graphics just, it think its intel extreme

nino

---

### Post by anil_robo on 2005-12-17
You may have messed up with your configuration files "copying and pasting" from some tutorials in this forums ;)

I have Dell Inspiron 6000 and closing its lid always puts system to sleep, and wakes it up perfectly when opening the lid! :)

---

### Post by ninocass on 2005-12-18
i think i may have done lol so far ive reinstalled ubuntu 4 times through my messing, man a system restore would be good ;) ;)

---

### Post by anil_robo on 2005-12-19
[quote=ninocass]i think i may have done lol so far ive reinstalled ubuntu 4 times through my messing, man a system restore would be good ;) ;)[/quote]
I support your view nino! In fact, it may already be there, just that we don't know how to do it from terminal! ;)

---

### Post by Confuse on 2005-12-23
I have this problem and can't get rid of it. I have the I6000 with intel graphics. It goes to suspend just fine but it doesn't come back. The screen is just blank and unresponsive.

---

### Post by ninocass on 2006-04-05
sorry foir diging up an old post but the problem seems to have reared its ugly head once again!!!

to recap when i close my lid, the screen dosent wake up but i still have control of the computer, i just cant see anything!!

I dont want to do another format as i have fluxbox all set up and a load of programs installed 

Cheers

Nino

---

### Post by anil_robo on 2006-04-05
[quote=ninocass]to recap when i close my lid, the screen dosent wake up but i still have control of the computer, i just cant see anything!![/quote]
It "seemed" to be the same case with me... until the time I moved the mouse pointer. It appears that keyboard input wasn't able to rid me off that black screen - all it required was some mouse movement! :)

Check yours! Move mouse when the black screen comes! :)

---

### Post by jchau on 2006-09-30
In case anyone stumbles upon this thread in the future, here is the solution. [http://ubuntuforums.org/showthread.php?t=134319](http://ubuntuforums.org/showthread.php?t=134319)

---

