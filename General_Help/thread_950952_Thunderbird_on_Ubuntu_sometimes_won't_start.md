---
title: "Thunderbird on Ubuntu sometimes won't start"
date: 2008-10-17
forum: General Help
---

### Post by Rocktman2 on 2008-10-17
I've posted this problem on 3 other on-line forums (1 is the Mozillazine forums). I got a response from another user who has the same issue. He has a workaround, but no solution. I hope someone here can help me. 

I've been trying to get Thunderbird to work reliably in Ubuntu 8.04.1 w/o much success. The problem is that TB will not consistently startup. When I first boot into Ubuntu (I dual-boot with Window$), TB will usually startup, but not again after exiting. I'm using -profilemanager, which does startup every time, but clicking the "Start Thunderbird" button seems to have no effect, other than to have profilemanager exit (this is after the first startup). I have installed, uninstalled, reinstalled TB 3-4 times with the same results from Add/Remove Applications. Originally, I had the Folderpane Tools extension installed that I thought was causing the problem. I uninstalled it, but the problem remained. Also tried a new profile & safe mode without success.

Now here's the weird part (maybe yes, maybe no): if I have either Firefox or Sunbird running, TB seems to startup every time. Right now I have the Webmail & Yahoo extensions installed, but the problem predates their install.

Is this known issue with TB on Ubuntu? Anybody have any ideas?

---

### Post by quibbler on 2008-10-18
Have you tried uninstalling Thunderbird, then deleting the hidden folder
in your Home directory .mozilla-thunderbird? If not do that and then reinstall.
Your problem may be a corrupy profile.

Regards quibbler

---

### Post by CHW on 2008-12-14
Hello,

I have a similar problem:
When I boot into Ubuntu, TB not always starts. I'm using Ubuntu 8.10 but I had this problem already in Ubuntu 8.04. (no dual boot with another system)
I'm using two extensions with TB: "Fire Tray" (Version 0.1.11) and "Lightning" (Version 0.9).

I tried to re-install everything but without success.
Then I read this thread some weeks ago and decided to create a new profile.
I found this page:

[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird)

and did what was described there, but the problem still persisted.
Today I decided to delete this folder again and configured everything by hand, I only imported my mails and the address book but after the third trial-reboot it didn't startup and I decided to ask here for help.

Regards,
CHW

---

### Post by CHW on 2009-01-06
bump

---

### Post by WhiteSphinx on 2009-05-27
:D**MY THUNDERBIRD PROBLEM SOLVED**:D

I could not get Thunderbird to start from profilemanager. I reinstalled the program, I searched for fixes, finally after a lot of experimenting I came up with this:

I put two Thunderbird launchers on the upper panel. The first one opens profilemanager and the second one launches Thunderbird (with the %u parameter). I pick the profile first. When profilemanager disappears from the screen (it stopped launching the email client a long time ago), I click on the second launcher and it opens Thunderbird in the profile that I had just picked using the first launcher.  It works every time. ;)

---

