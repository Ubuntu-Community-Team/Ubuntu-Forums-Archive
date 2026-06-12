---
title: "Upgrade from 9.10 RC"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by gdonwallace on 2009-10-29
OK, so I downloaded and installed the RC last week.  I've done a couple updates during that time, thinking that things are getting fixed for the upcoming final release.

So I get the email to do the update.  Follow the instructions about running update manager and it should offer the option to update to the latest release, but I don't get that option.

Just wanting to make sure that this is not an issue with update-manager, that I am actually running the final release.

---

### Post by Joeb454 on 2009-10-29
If you installed a prerelease version of Karmic (9.10) and kept it updated, then yes, you will be running the final release :)

For example I've been running since alpha 6 with the same install :)

---

### Post by NormanFLinux on 2009-10-29
Correct. If you've ran the 9.10 beta on various versions of Ubuntu, you were updated last week to the RC which in effect is the final release that came out today. You will only get notified of a distribution upgrade when running a previous version of Ubuntu.

---

### Post by ShaneR on 2009-10-29
So, are you saying where I just installed the RC yesterday, and ran whatever updates where available, that I am completely updated and should not expect any further for today's release?

---

### Post by susanw on 2009-10-29
This thread is the same as the thread:

[ubuntu] 9.10 beta to full version

But with  a few more answers. 
Is there a way to know whether a beta version is the new version or do they literally convert (in name only if no changes) into actual version with no notification? If so excellent, the easiest upgrade yet!

---

### Post by NormanFLinux on 2009-10-29
I think its a silent upgrade:

I ran in Konsole the command sudo apt-get update && sudo apt-get dist-upgrade. It reported no packages to upgrade in 9.10 beta.

---

### Post by groetz on 2009-10-29
Hi,
On the top toolbar, click System, About Ubuntu, and it will tell you what flavor you are running... in my case: "You are using Ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011."
	
I loaded 9.10 RC yesterday and it upgraded itself to 9.10

---

### Post by Jugney on 2009-10-29
An illustrative thread.

I downloaded the RC on Friday, and am going to install 9.10 for a friend, so naturally I thought I'd wait til the official release came out. But it sounds like I don't need to burn another CD - simply doing the regular system updates will make up for the difference between the two.

The Koala ROCKS!!!

---

### Post by fancypiper on 2009-10-29
This command should show you, or use the System Monitor's first tab.
cat /etc/issue

---

