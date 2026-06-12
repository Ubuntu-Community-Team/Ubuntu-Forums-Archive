---
title: "Attempting to upgrade a Dell Inspiron 15 from 14.04 to 17.04, hardware issues."
date: 2017-10-10
forum: Hardware
---

### Post by hawk-v3 on 2017-10-10
I bought a Dell Linux Laptop. [https://certification.ubuntu.com/hardware/201504-18248/](https://certification.ubuntu.com/hardware/201504-18248/) This one in particular, it came with a Dell version of 14.04 on it, and really, truly was a pain to try and install 17.04 on as the liveCD would work fine, but the installer would just be black. I solved that one.

After some faffing around with nomodeset in the GRUB launch options, I'm currently booting both 14.04 and 17.04 off one SSD that I swapped into it.

The laptop works in 17.04... Sort of. I'm having multiple issues, some of which were prevalent in the 14.04 and I'm asking about in hope that I might get an answer, and some which were working in the older version but don't in the new one. So, in order:

Issues on both systems.

[LIST]
[*]Laptop will not remember settings like screen brightness level, bluetooth state (I'd like it to be off by default) or programs meant to run at the laptop's booting (like Redshift.)
[/LIST]

Issues on 17.04.
[LIST]
[*]Laptop is really, heavily slow. Granted, the 14.04 install is a little sluggish, but this one really, really chugs.
[*]Laptop has no screen brightness control whatsoever.
[*]Laptop doesn't appear to have proprietary drivers that the 14.04 install had, but this might just be due to updates?
[*]Minor, but annoying: Touchpad has flipped it's direction and behaviour of scrolling.
[/LIST]

I suspect I'm possibly missing some packages that would make my life easier, but I... Don't seem to have any good google-fu when it comes to trying to find hardware packages for this setup.

I'm not new to linux/ubuntu, but I've not had issues before, so I'm kind of bumbling in the dark here. If people need more information I'll gladly post it. If you can help me, I'll be most grateful, and I apologise if this isn't quite how this question should be phrased.

Thanks for your time.

---

### Post by Autodave on 2017-10-10
First off, with only a 1.6 processor, I would probably be looking for a lighter version such as Xubuntu. I could not find how much RAM is in that machine, but that would also be handy to know. Also, since you are having some problems, I would be looking at installing a long term release (LTS).

  	 	 	 	   Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by oldfred on 2017-10-10
Dell with just about every new generation has new drivers & releases Sputnik. But later versions of Linux include those drivers.

 Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/) 

My 2006 Toshiba laptop was low powered. With Unity in 12.04 it was so slow as to be unusable. But I installed fallback/flashback/gnome-panel (name changed with versions) and that is like the old gnome2 with menus & much lighter weight. You can add that with this command and select it when you reboot on enter password screen.
      
 sudo apt-get install gnome-panel 

But most would suggest one of the lighter weight flavors/versions of Ubuntu.
      
 Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie

---

