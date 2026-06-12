---
title: "Suspend is a Hypocrisy"
date: 2008-05-03
forum: Hardware
---

### Post by schmolch on 2008-05-03
Since years Linux pretends to support suspend to ram and suspend to disk.

The reality is that is does not work for most people, no matter of the brand of the laptop or the age.
I have 5 thinkpads myself and none works except for the 12 year old apm-model which is no suprise of course.

If Suspend works half the time its useless, unless it works reliably it practically does not exist.

PLEASE STOP PRETENDING TO SUPPORT SUSPEND, IT IS A LIE and just frustrates people who cant get it working.

The least we can ask for is a warning that says "Usually does not work, dont bother too much".

---

### Post by Keyper7 on 2008-05-03
While I agree that suspend and hibernate do not work for a lot of people, I cannot agree with your post unless you give a reference to an official statement from the Linux kernel team or Canonical saying that suspend will always work regardless of the machine.

A lie is a statement that contradicts reality. If it's never been stated, it's not a lie.

This is a very important problem, but insulting the developers and calling them liars does not accomplish anything.

---

### Post by bmac on 2008-05-03
Similar to many post you sound really frustrated. Not all applications work with all hardware under Ubuntu. I've noticed many people have managed to get this function operational however, you have not. With all the hardware available and different systems I can imagine writing code to cover every make, model and unique system would be extremely taxing. Plus many of the apps require drivers from the manufacturer, which in it self would be an extraordinary complex endeavor. Especially, when most of these vendors target M$ as their primary OS. 
My only recommendation is to report the bug and be patient until the team can resolve the issue. Should you decide this particular issue is mandatory for your system then perhaps Ubuntu isn't presently the appropriate OS for your PC.
I can tell you I've been using Ubuntu since Fiesty and have experienced almost zero major problems since day one (some minor issues). Plus I realize it isn't Window and don't expect it to function like Windows. I can't count the number of blue screens received in windows or how many times I searched to find Windows drivers on the net that still didn't work. I don't believe any OS today solves all the problems, nor have I heard Ubuntu claim they can.
Tolerance should be the key word when negotiating with any new OS. Including Hardy...

---

### Post by dale_nx26 on 2008-05-03
I agree with keyper, "Dont get mad, get glad." hehe. Anyways, yea, hibernate and suspend don't work for me either, but I'm hopeful i'll find a solution or eventually more drivers are released or hardware supported. In response to bmac, I always find the drivers I want for Windows. Actually everything is mostly perfect in that realm for me. My only complaint is how Windows mysteriously conjure up minor bugs and how it has slowed down after I installed Ubuntu. Windows and Ubuntu are fairly equal in terms of stability for me.

---

### Post by schmolch on 2008-05-04
You guys are not getting it.

There is quality control for everyhing else on the Desktop.

Hardy does not run a gnome version from cvs/subversion.
Hardy does not run a kernel that has been coded the night before.

Why is that?
Its to make sure that things run as good and as reliable as possible because otherwise the system would be a agglomeration of unstable **** that does not work for anyone.

This quality control does not apply to Suspend.
Suspend is part of the default Desktop since years and its still not ready. Suspend does not work for MOST people.
There is a hugge difference between "not working for everybody" and "not working for MOST people".

Im not even complaining about the fact the suspend is not working, this is neither Ubuntu's nor the Kernel's fault.
It's the fault of acpi and all the ******* companies that don't give a **** about sharing specifications and working together to increase the quality of all our computing experiences.

Im complaing about the fact the there are suspend buttons on everybody's desktop AS IF THIS WOULD WORK, which is not the case.

Stop pretending, that's all i want.

---

### Post by Keyper7 on 2008-05-07
I did get your point.

The problem here is semantics. What "supported" is supposed to mean? All suspend and hibernate steps ARE implemented in the kernel and are supposed to work. Like you said yourself, this is mostly the fault of buggy BIOSes and ACPIs, and bad support from hardware vendors. We cannot ask the developers to hunt those cases down and put if(biosisacrappybios) in the code, this is bad programming.

Furthermore, it's made very clear that proprietary blobs are not fully supported. If it's true that the majority of people have problems with suspend and hibernate, it's also true that the majority use proprietary drivers. Complaints should also be sent to nVidia and ATI.

Bottom line, I don't call the current situation a pretense. I don't think it would make much sense to remove the buttons or put a warning. The suspend mechanisms in the kernel are not incomplete. I think what you're doing is not very different than calling the gedit developers pretenders for not putting a warning in gedit saying "Warning, this editor might not work properly if some keys on your keyboard are missing".

---

