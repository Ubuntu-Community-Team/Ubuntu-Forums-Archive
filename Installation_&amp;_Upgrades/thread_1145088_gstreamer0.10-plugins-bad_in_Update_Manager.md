---
title: "gstreamer0.10-plugins-bad in Update Manager"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by Spartachris on 2009-05-01
After I upgraded to Jaunty from Ibex the Update Manager has gstreamer0.10-plugins-bad gray-ed out in the top box. I cannot check the check box, and when I check for updates, it's not grayed out, but still cannot clear the box.

I'm a noob, so I don't know what that package is, if I need it, or how to clear it.

Thanks for your help!

---

### Post by zigga15 on 2009-05-01
In synaptic click edit > fix broken packages --- see if that helps.

---

### Post by patslap on 2009-05-01
I have a similar problem with gstreamer0.10-plugins-bad being greyed out, and liblucene2-java greyed-out, too.

The suggestion in the post above did not work for me. 

Any other ideas?

Thanks in advance.

---

### Post by zigga15 on 2009-05-01
sudo apt-get autoclean

or

sudo apt-get dist-upgrade --fix-missing

or

dpkg -i --configure

and if this fails

dpkg -i -f --configure

keep googling for "fixing broken packages"

---

### Post by ozite on 2009-05-05
I had this same problem.  Go to Synpatic Packager Manager.  Check for any items under Installed (upgradeable).

---

### Post by yamakake on 2009-05-09
Thanks ozite!  It worked!

---

### Post by daqron on 2009-07-18
As usual, I figured out what gstreamer is and how to fix this problem the hard way. Gstreamer is a video/audio codec library. You probably need it. And for reasons passing understanding, the people who distribute the codecs have named the package "bad" even though by normal people's definition it is "good" (i.e., it lets you watch video podcasts and stuff).

So, if you go into Synaptic Package Manager, click on Custom Filters (lower left), then click on Upgradable (Upstream), you should see the gstreamer package, which you should then mark for installation. After you apply the change it should disappear from the upgrade manager.

---

### Post by funajo on 2012-02-22
In Ubuntu select System > Administration > Synaptic Package Manager.
Using "Quick Search" find "ubuntu-restricted-extras" and select for installation choosing to install all the recommended packages. and wala! done!.

---

### Post by funajo on 2012-02-22
In Ubuntu select System > Administration > Synaptic Package Manager.
Using "Quick Search" find "ubuntu-restricted-extras" and select for installation choosing to install all the recommended packages.

You dont need to upgrade. do not uninstall gstreamer0.10-plugins-bad.

---

### Post by nothingspecial on 2012-02-22
Old Thread

Closed

---

