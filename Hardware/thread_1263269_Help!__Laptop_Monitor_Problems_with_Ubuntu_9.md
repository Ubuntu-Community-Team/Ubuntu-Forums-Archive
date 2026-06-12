---
title: "Help!  Laptop Monitor Problems with Ubuntu 9"
date: 2009-09-10
forum: Hardware
---

### Post by glennhd on 2009-09-10
I just rebirthed my Dell Latitude X200 by deleting Windows and installing Ubuntu 9.04.  The install went well and most everything functioned properly.  

However, after about 10 minutes, the letters on my LCD laptop display begin to fill in dark until after another 5 minutes all the lettering is filled in and I cannot read the screen.

I fooled around with the display settings but that didn't help.  It's now set at 1024 x 768.  Even at 800 x 600 the same occured.  I thought it might be the refresh rate which is preset at 60HZ.  Normally this should be higher.  However, one cannot adjust it in this dialogue.

Has anyone ever had this problem and can you tell me what I can do to eliminate the situation?  Obviously, the computer becomes useless after 10 - 15 minutes.  Any help would be graciously appreciated.  I'm a new user to Linux but savvy with Windows.  Linux is so much better.  I'd really like to use it.

Thanks all!

Glennhd:guitar:

---

### Post by thegreatsnafu on 2009-09-10
What?:confused: Letters fill up your screen? Please explain...

---

### Post by overdrank on 2009-09-10
> **glennhd said:**
> I just rebirthed my Dell Latitude X200 by deleting Windows and installing Ubuntu 9.04.  The install went well and most everything functioned properly.  

However, after about 10 minutes, the letters on my LCD laptop display begin to fill in dark until after another 5 minutes all the lettering is filled in and I cannot read the screen.

I fooled around with the display settings but that didn't help.  It's now set at 1024 x 768.  Even at 800 x 600 the same occured.  I thought it might be the refresh rate which is preset at 60HZ.  Normally this should be higher.  However, one cannot adjust it in this dialogue.

Has anyone ever had this problem and can you tell me what I can do to eliminate the situation?  Obviously, the computer becomes useless after 10 - 15 minutes.  Any help would be graciously appreciated.  I'm a new user to Linux but savvy with Windows.  Linux is so much better.  I'd really like to use it.

Thanks all!

Glennhd:guitar:
Hi and welcome, if you are using the intel graphics then you may look at the link in my signature about intel graphics in Jaunty.
You may use this command in the terminal ```
lspci | grep VGA
``` to identify your graphics. The terminal is located under applications, accessories.

---

### Post by glennhd on 2009-09-10
> **thegreatsnafu said:**
> What?:confused: Letters fill up your screen? Please explain...
The letters just become dare and unreadable.  Similar to highlighting but with black.  Then, the sentences are all just black lines.  This occurs with each program.  However, it is progressive and begins about 15 minutes into the session and gets worse over the next 15 minutes.  Thanks!

---

### Post by thegreatsnafu on 2009-09-11
Hmm, this seems to be some kind of strange software problem. I know it may be a long shot but, check your power settings, see how long it takes for the screen to turn off. I would also check the screen saver settings to see how long it takes to turn on. If they are set to trigger at about 15 minutes, then that may be your problem. It also could just be compiz that is causing the problems.

---

### Post by glennhd on 2009-09-11
> **thegreatsnafu said:**
> Hmm, this seems to be some kind of strange software problem. I know it may be a long shot but, check your power settings, see how long it takes for the screen to turn off. I would also check the screen saver settings to see how long it takes to turn on. If they are set to trigger at about 15 minutes, then that may be your problem. It also could just be compiz that is causing the problems.
Thank you very much.  I never thought about this but it could the problem.  I'll try to extend the screen shut down as well as the screen saver and we'll see what happens.  Right now, I've really fooled with the Appearance items and while the printing does not look great, it has increased the time before the characters go dark. 

I'll also check the compiz.  What would you suggest concerning compiz.  Is there a command line I should use?  Being new to Linux (newb) I need some direction here.  You're help is appreciated.  

Many thanks friend!

glennhd

---

### Post by thegreatsnafu on 2009-09-11
Here is the easiest way to turn off Compiz:


[LIST=1]
[*]Right click on the desktop and select "Change Desktop Background" -OR- Go to "System" -> "Preferences" -> "Appearance".
[*]Go to the "Visual Effects" Tab.
[*]Click "None".
[*]Then Compiz should be turned off...
[/LIST]

---

### Post by thegreatsnafu on 2009-09-13
Just checking in. Are your problems solved? If not, then I'm always glad to help!:)

---

