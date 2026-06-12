---
title: "Do I have a virus?"
date: 2008-07-23
forum: General Help
---

### Post by rmjohnson144 on 2008-07-23
I just got some updates today and they were for a server type program called userspace.  I know that a lot of virus programs install servers to create junk mail on your system and was wondering if this is what's happening or is this part of ubuntu and a normal update?

-=Mark=-

---

### Post by WRDN on 2008-07-23
If you downloaded the updates from the repositories then, they are NOT viruses, as the maintainers check all files before placing them in the repositories.
You don't need to worry about security really.

---

### Post by H3retic on 2008-07-23
[http://www.userspace.com/](http://www.userspace.com/)

This userspace?  What makes you think you have a virus?  Please state some 'symptoms'.

Alternately, you can install clamAV from the install application and do a virus search.

---

### Post by Elfy on 2008-07-23
look in synaptic history it's in one of the menus - see which package was updated in the for thepackage name - you should be able to check in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for it and see it's changelog.

---

### Post by billgoldberg on 2008-07-23
> **H3retic said:**
> [http://www.userspace.com/](http://www.userspace.com/)

This userspace?  What makes you think you have a virus?  Please state some 'symptoms'.

Alternately, you can install clamAV from the install application and do a virus search.

Correct me if I'm wrong but there aren't any linux viruses out in the wild.

Also, doesn't ClamAV (and all other virus scanners for linux) scan for windows viruses. So you don't pass them along to other people?

I'm pretty sure they do.

--

If you are updating your system and haven't added any dubious repo's, you will be fine.

---

### Post by Kevbert on 2008-07-23
I think there's a bounty on finding a linux virus in the wild.  ClamAv is only good for DOS/Windows viruses.  The only reason for using it is if you share files with Windows/DOS (including email attachments).

---

### Post by rmjohnson144 on 2008-07-23
Thanks again for such quick responses.

The only reason I suspect a virus is I have visited some questionable websites.  ubuntu seems fines and is running great!  I just didn't remember seeing this userspace thing being installed when I used Synaptic.  I thought maybe a virus tricked ubuntu into installing it.  

ok, looking at updates it looks like it is GVFS that is being updated.  It just says in the description, "userspace virtual file system - server".  I see several other updates to it as well and it seems to be some sort of file system, so maybe it isn't a mail server.  It looks to be some sort of way to mount different filesystems.  I guess I should have googled a little better.  I guess I'm just paranoid.  I've been getting so many viruses lately that I guess I'm a little spooked.

I wish I could get all my programs running in ubuntu so I can dump windows!

thanks again for the help
-=Mark=-
ps. will wine run vista stuff and dx10 yet?  I know, I'm asking a lot.

---

### Post by knutschr on 2008-07-23
When using Linux, be free to open as many questionable websites you want without fear :-)

---

### Post by tamoneya on 2008-07-23
really the only sort of unwanted crap you could have is a rootkit.  Install rkhunter to make sure although I highly doubt you got one.  
```
sudo apt-get update
sudo apt-get install rkhunter
```

---

### Post by WRDN on 2008-07-23
> **rmjohnson144 said:**
> 
ps. will wine run vista stuff and dx10 yet?  I know, I'm asking a lot.

You can run Vista in VirtualBox or another Virtual Machine, but you can't run DX10 or DX10 games as far as I know.

---

### Post by LowSky on 2008-07-23
> **knutschr said:**
> When using Linux, be free to open as many questionable websites you want without fear :-)

NOT TRUE: In most cases (99.99999% of the time your safe) but attacks can still occur and because you can set blank password (idiot if you do) dont think that linux can be entirely safe. I know that at the moment Linux is safer than say Windows, but where there is a will there is a way. At the moment there is no one willing to create viable linux viruses, Remember even the most security concious nations get breached (like the US, UK or Isreal). Think of Linux as if it was a small country like Bermuda, and America like Microsoft --- People always go after the bigger fish not the guppies. No offence to the fine people of Bermuda. :guitar:

---

### Post by knutschr on 2008-07-23
Well. I don't think he has a blank password :-)
Have you ever heard of a normal Linux user being infected of whatsoever?

To make an intrude into a Linux box many are trying, because of the power of a Linux machine.

One linux machine can be made to control millions of Windows machines.
A Windows machine can't do this.

---

