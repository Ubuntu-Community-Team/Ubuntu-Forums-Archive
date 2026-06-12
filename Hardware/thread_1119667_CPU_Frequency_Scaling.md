---
title: "CPU Frequency Scaling"
date: 2009-04-08
forum: Hardware
---

### Post by SnackMasterX on 2009-04-08
Hello,

I am using a desktop at work which will be commonly performing CPU intensive activities and was wondering if there was a way to disable CPU frequency scaling.

Thanks in Advance!

---

### Post by mtbsoft on 2009-04-08
Right click the top taskbar, select *Add to panel...* then select the *CPU Frequency Scaling Monitor* and press the *Add* button.

Once installed, simply click the applet and select the desired frequency or profile to lock it into that mode until the next boot - *Performance* would probably suit you.

Easy peasy...

---

### Post by stchman on 2009-04-08
> **mtbsoft said:**
> Right click the top taskbar, select *Add to panel...* then select the *CPU Frequency Scaling Monitor* and press the *Add* button.

Once installed, simply click the applet and select the desired frequency or profile to lock it into that mode until the next boot - *Performance* would probably suit you.

Easy peasy...

That is just a monitor.  That app does not modify the frequency scaling of the processor.

---

### Post by stchman on 2009-04-08
> **SnackMasterX said:**
> Hello,

I am using a desktop at work which will be commonly performing CPU intensive activities and was wondering if there was a way to disable CPU frequency scaling.

Thanks in Advance!

No need to disable frequency scaling.  If you are doing processor intensive tasks then the algorithms that control frequency scaling will run the processor at 100% speed.

Frequency scaling is intended for when the processor does not need to run at 100% it won't.

---

### Post by Thermalpaste on 2009-04-08
Goto system > administration > snyaptic package manager and install powernow daemon. 

Open terminal and type powernowd -h ; will give you all necessary parameters to control cpu throttling.

---

### Post by N_Nick on 2009-04-08
Well if by "a way to disable CPU frequency scaling" he meant constant 100% CPU speed i think the CPU Frequency Scaling Monitor can do that.

---

### Post by mtbsoft on 2009-04-08
> **stchman said:**
> That is just a monitor.  That app does not modify the frequency scaling of the processor.
Sorry, but you are wrong - it enables the user to select a CPU speed or performance mode and fix that until the next reboot.

Since the original poster wanted to disable scaling i.e fix it to a particular speed, in his case high, then is DOES do what is required.  I know this because I use it for just that purpose myself.

---

### Post by PreviousN on 2009-04-08
God you people. Without being mean, please only help if you know that what you suggest will actually help. Have you ever done this yourselves? Please stop distributing incomplete information, or asking the OP to install something that isn't needed. 

Here's how you activate the ability to set your own cpu scaling. 
1. Open a terminal
2. Type: "sudo dpkg-reconfigure gnome-applets"
3. The terminal will ask if you want to install the cpu scaling applet with suid root. Choose yes. 
4. Now you can add the cpu frequency scaling monitor to the gnome panel, and have the ability to change (or set) the frequency.

Just adding the monitor without reconfiguring the applet provides just that: a monitor.

Sorry for being so grumpy. I'm not trying to be a jerk.

---

### Post by mtbsoft on 2009-04-09
> **PreviousN said:**
> Have you ever done this yourselves?
Erm, if you read my post you'd see the answer is a very clear YES; the question is... have you?

> **PreviousN said:**
> Just adding the monitor without reconfiguring the applet provides just that: a monitor.
IF that were the case, how do you explain the fact that I have never done what you state and yet I have the "monitor" installed on many of my boxes, offering me various speed options and they DO work.  It is not necessary to do as you state unless, perhaps, you are logged in as an unprivileged user.

Furthermore, I've just confirmed it on a brand new install (8.10) which I built two days ago, Dell mini 9, still vanilla as I haven't configured it for what I want yet. Installing the applet in the manner stated and selecting a different profile, it displayed the Authenticate dialog "Privileges are required to change the CPU Frequency scaling".  Authenticating then permitted the CPU scaling mode and/or frequency to be changed.  Running xengine(or any other simple benchmarker) will confirm the CPU mode change.

So unless the privilege portions of the O/S (and the benchmarker and Conky and the general behaviour of the computer) are all lying, the advice I gave IS valid and does provide the functionality the OP requested.

As for you last statement, reread your own first line please...

---

### Post by mister_playboy on 2009-04-10
I know that scaling "on demand" does not work correctly with Folding@Home... so I would set it manually with the applet when needed to be safe.

---

### Post by PreviousN on 2009-04-11
Yes I was (barely) a jerk. I knew it and apologized for it. At the same time, it's important that new users don't get incomplete advice and stuck running around trying several things that won't solve their problem. I was merely offering my annoyance at the fact that the user was getting incomplete advice for an easy fix.

I'll think twice next time before I say "god" and offer the exact steps one would need to fix a problem they are having. Good day to you sir.

---

### Post by dolphin_oracle on 2009-04-11
PreviousN,

thanks for the info on the applet.  I was personally was having trouble with the scaling feature.  

Thanks.

D.O.

---

### Post by mtbsoft on 2009-04-11
> **PreviousN said:**
> Yes I was (barely) a jerk. I knew it and apologized for it. At the same time, it's important that new users don't get incomplete advice and stuck running around trying several things that won't solve their problem. I was merely offering my annoyance at the fact that the user was getting incomplete advice for an easy fix.

I'll think twice next time before I say "god" and offer the exact steps one would need to fix a problem they are having. Good day to you sir.
You still don't get it, do you?  You still can't/won't accept that you were not the only correct poster in the thread.

In future please simply state, without rhetoric or emotion, what you believe is wrong and how you believe the matter may be corrected, that way things do not get out of hand and the original post lost in the trail of argument and counter argument.  

Most of all, please don't dismiss another poster's opinion until you can **prove** beyond reasonable doubt that they are not correct - just because one way works for you doesn't mean it works for others and that there ane not alternative ways too.

---

### Post by rainwalker on 2009-05-13
For anyone still having trouble with this, installing "powernowd" did the trick for me.

---

