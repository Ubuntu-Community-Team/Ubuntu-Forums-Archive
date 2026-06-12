---
title: "Complete Newbie"
date: 2013-07-10
forum: Hardware
---

### Post by Joe West on 2013-07-10
I run a church office in Houma, Louisiana.  I have three computers, two laptops and one fairly new Gateway All-In-One.  Windows has cost me handsomely in errors, down-time, virus', trojans and the list goes on.
I need to get Linux on all three machines, and only one will have a windows presence, for compatibility sake of software already out there.
I need to learn about software for linux to do the things I used to do in windows.  Suggestions are welcome.  I have no problem supporting the linux project, or paying for software.;)

Joe West

---

### Post by VMC on 2013-07-10
Shortly you will get many responses. In the mean time, I would ask. Are these computers on a LAN together? Do you want to use Ubuntu Server? Are you wanting to run both Windows and Ubuntu, or rather to be able to boot either one?

There's several directions to go. One simple solution is to install Ubuntu on each PC. A server solution will take some time to find the best solution.

Edit: My best advice is to install Ubuntu on one as a test at first, then once comfortable with using Linux migrate the others as well.

---

### Post by snowpine on 2013-07-10
I agree with VMC; install Ubuntu on one machine on a trial basis (as a "dual boot" with Windows). 

Once you have some experience with Ubuntu you can make a more educated decision whether it is the right solution for your computing needs.

---

### Post by QIII on 2013-07-10
I have to echo both VMC and snowpine.

You might find that the difficulty and expenditure of resources to learn a totally new way of doing things after having thrown all of your eggs in that basket is greater than the problems from which you are trying to escape.

You can't be of the mind that simply moving to Linux will "fix everything".  It won't. Linux is not a panacea or a drop-in replacement for Windows. It is an alternative.

There are a couple of slightly different approaches you might consider as a way to familiarize yourself with Linux before you leap:  

1.  If your Windows machines are "Professional" or "Ultimate", you can use Remote Desktop Protocol (RDP) to access their desktops as if you were sitting at them.  Install Ubuntu on one machine, not dual-booted. That leaves you with two Windows machines.  Install remmina and the RDP plugins on your Ubuntu machine.  You can start a new thread to get the details.  This would allow you to have one machine dedicated to Ubuntu without the mess of dual booting, but still allow access to Windows when you need it.

2.  Install Ubuntu in a virtual machine (Virtualbox, imperfect as it is, is free) in Windows and learn it there.  If you break it, you won't put the machine out of action.  You can re-install/repair the virtual machine to your heart's content until you have developed some familiarity.

Test the water before you dive in.

Best wishes!

---

### Post by Mark Phelps on 2013-07-10
One additional caveat about making the jump ...

You mention "church office" -- so I presume that you will want to install and run software with that in mind.  IF this is true, the problem is not going to be one of being able to afford the software; instead, the problem is going to be one of even being able to find such software that will run in Linux.

Same is true, but to a lesser extent, of more generic "office" software.  If you're using MS Office today and are willing to learn new interfaces and new ways of continuing to do office-related work in Linux apps, then you're in good shape.  But, if you will be needing to continue to use MS Office file formats (such as the xml versions of Excel spreadsheets, Word documents, or PowerPoint slides), then your move to Linux will be a difficult one -- as only MS Windows really provides first-rate support for MS Office files.

It's not that you can't do the same activities in Linux as you did in Windows; it's more that you will have to learn all new ways of doing those -- which is a strong reason for converting one machine, and "learning the ropes" in using Linux apps before you make a total switch.

---

### Post by Cheesehead on 2013-07-10
> **Joe West said:**
> I need to get Linux on all three machines,
[....]
I need to learn about software for linux to do the things I used to do in windows.



The most successful transitions I have seen start by replacing software on the Windows machines with multi-platform-compatible alternatives. Replacing applications and changing the workflow are much bigger hurdles than replacing the operating system.
For example, replacing Internet Explorer with Firefox
For example, replacing Outlook with Evolution
For example, replacing MS Office with LibreOffice

After users are comfortable with the new software, and have fixed the disruption to their workflow, then you can install Ubuntu with the same applications. 

Issues that pop up in transitions like these:
- User accounts. Each user should have their own secure account, and you're stuck being the admin. It's a pain, but do it right. It causes a lot more pain later if you don't. Should everyone have an account on each machine? Should everyone's desktop be stored centrally so it doesn't matter which machine they log into? Will members of the public have access to the machines (Guest account)?

- Sensitive Data. Member lists, evaluations, financial documents, etc. Identify them and figure out who should have access to them, and how you want to store them. For example, an encrypted folder on a shared drive or server.

- Backups. User data, shared data, encrypted data, etc. Good backups are incremental, redundant, and off-site. Linux also makes them very easy...once you decide what you want.



What you can do today, for free:
1) Download and install replacement applications. You don't need to remove the old ones. Get people started using them.
2) Create a LiveUSB, and boot each system into Ubuntu (risk-free) to test your hardware. DON'T install Ubuntu today.
3) Look around for a local Linux user group. They can help you a lot, too.

---

