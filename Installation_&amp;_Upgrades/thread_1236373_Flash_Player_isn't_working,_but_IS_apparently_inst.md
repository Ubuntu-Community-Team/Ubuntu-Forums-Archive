---
title: "Flash Player isn't working, but IS apparently installed..help please!"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by atterkop on 2009-08-10
'Update Manager' popped up yesterday, so I set it running. Part of the way through, it froze.

Now, having an appointment to keep, I turned off the power, which may not have been the smartest move ever (with the benefit of hindsight).

My current problem is that Flash Player is no longer working, which leads me to surmise that it was a Flash Player update that froze during installation. However, when I have since tried to reinstall it from the Adobe website, (following the instruction given there) the installer window indicates that it is already installed.

However, when I try to install it with Update Manager, I receive the following error message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have attempted to run this, but Terminal does not recognise the 'configure' part of the command.

Needless to say, websites that require Flash support do not work as they should.

Apologies for this rambling post, and the lack of appropriate terminology, but I am not particularly used to dealing with problems of this type, and would be very grateful for any advice that may be offered.

---

### Post by phillw on 2009-08-10
Sounds like flash is corrupt ...

Try going into Synaptic Package Manager (System ==>  Administration)

Type in flash .. 

[IMG]http://ubuntuforums.org/home/phillw/Desktop/Screenshot-Synaptic%20Package%20Manager%20.png[/IMG]look for flash-plugin installer  (should have a green box next to it)

Mark it for re-installation

[IMG]http://ubuntuforums.org/home/phillw/Desktop/Screenshot-Synaptic%20Package%20Manager%20-1.png[/IMG]
Then select 'apply' - this should get you back up & running

Regards,

Phill.

---

### Post by tomasrey88 on 2009-08-10
go to add/remove programs, click on "all applications", type in flash, uninstall flash, turn off computer, turn on, reinstall flash, turn off computer, turn on, enjoy. 

:guitar:

I've answered your question, please take a look at mine coding jedis: 
[http://ubuntuforums.org/showthread.php?p=7762391#post7762391](http://ubuntuforums.org/showthread.php?p=7762391#post7762391)

Thanks,
:-)

---

### Post by atterkop on 2009-08-10
Thanks for your suggestions guys, but I'm still stuck..

phillw: I've done as you said, but the window says"configuring", and seems to be stuck there. I'll leave it, but it's been half an hour already with no sign of movement...

tomasrey88: When I try your suggestion, I get the error message that I mentioned in my original post, and can go no further. Any ideas?

Once again, I really appreciate you  both taking the time to help.

---

### Post by phillw on 2009-08-10
If Synaptics Package Manager is not working I can only think of trying it at the command line with apt-get

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/)

has the how-to, remember to shutdown firefox !!!!

Let us know how you get on.

Regards,

Phill.

---

