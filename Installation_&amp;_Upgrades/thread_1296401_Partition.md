---
title: "Partition"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by olmo47 on 2009-10-20
OK!

I will give another try? about 2 years ago I have try to install another version, and I had the same treble! Partition, Partition, and Partition problems.

I have download a page from your site about "how to...partition"
I have try via Vista/My computer/ manage and this is ware I can't understand:I have 194GB free via Manage will only aloud me 2507 MB to shrink.

I try the suggestion under: [http://help.ubuntu.com.....but](http://help.ubuntu.com.....but) that instruction scenario, is not what I encounter.

I try via Manual partition and give me also a error (don't remember) I live in Corvallis Oregon and no one local (not sure of any one) that could help, I try the University but no local sopport.

I follow the in you web site to prepare the computer before I install (e.g. defragmented)boot from the CD or in this case a DVD (reason I didn't had any blanks) but boot ok.

this is since last knit I spend riding you web site for help and suggestion. 

I would like to boot side by side with vista or better yet a partition of his own (obuntu in this case)witch ever is the best suggestion?

This is my last try any help please?

Olmo47

---

### Post by QIII on 2009-10-20
If your are in Corvallis and haven't found someone to help, you are looking in the wrong place!
  
  Contact these people....
  
  [EMAIL="linuxusersgroup@oregonstate.edu"]linuxusersgroup@oregonstate.edu[/EMAIL]


Before using the partition manager, defragment your disk at least twice using the Accessories in your current installation.  That will gather up all the bits and pieces of mess that Windows scatters helter-skelter around your drive and will allow the partition manager to find a larger area of contiguous space to create a new partition in.

---

### Post by olmo47 on 2009-10-20
Thanks

However, since I got the copy of Ubuntu 9.0.4 I contacted the people (I thought) in this department, talk to a fellow name Tylor and said to me (I have asking him help for Ubuntu) and said that they don't have support for this.

I will send a email to the address you give to see if maybe I send it to wrong deparment.

Thanks again

---

### Post by olmo47 on 2009-10-20
I send a email:

This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    [email]linuxusersgroup@oregonstate.edu[/email]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 5.1.1 <linuxusersgroup@oregonstate.edu>: Recipient address rejected: User unknown in virtual alias table (state 14).

---

### Post by oldfred on 2009-10-20
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

The following article by the How-To Geek contains useful information regarding resizing your Vista partition, and getting it to boot again.
Using GParted to Resize Your Windows Vista Partition 
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

But if you use Gparted make sure you uncheck the checkbox:

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

---

### Post by QIII on 2009-10-20
Try info here for Linux Users Group

[http://lug.oregonstate.edu/](http://lug.oregonstate.edu/)

---

### Post by olmo47 on 2009-10-20
> **QIII said:**
> Try info here for Linux Users Group

[http://lug.oregonstate.edu/](http://lug.oregonstate.edu/)

Thanks I will give a shot!

Olmo47

---

### Post by olmo47 on 2009-10-20
> **oldfred said:**
> Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

The following article by the How-To Geek contains useful information regarding resizing your Vista partition, and getting it to boot again.
Using GParted to Resize Your Windows Vista Partition 
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

But if you use Gparted make sure you uncheck the checkbox:

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Thanks

am not sure if I have that much of confidencs?

but will reed the web page you send.

olmo47

---

### Post by oldfred on 2009-10-20
Sometimes pictures help - these have screen shots:
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

Installing dual boot
[http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Herman has a variety of dual boot examples - even if not exactly your versions worth reviewing just to understand the process as the version differences are usually minor.:
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

