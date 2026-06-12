---
title: "Please help me get some files off a Ubuntu Virtual Machine"
date: 2008-09-27
forum: General Help
---

### Post by Matsta on 2008-09-27
Hi there,
So first off I'm a Mac guy and my command line knowledge is virtually next to nothing apart from the absolute basics.
Anyway I'm working on a clients website and I need to upload the files to our server. The clients IT man has set up a VMware image from [http://www.thoughtpolice.co.uk/vmware/](http://www.thoughtpolice.co.uk/vmware/) (Ubuntu server 8.0.4). Now he had set it up on the clients computer that when they click a shortcut, VMware player would launch (the client is using XP) and then you could access the website via a physical local ip address. Now when I got the image, it was in a saved state and ifconfig was running which showed that there was a ethernet connection. When I restarted the VM, and did ifconfig the ethernet connection disappeared. So now it can't access the net at all :(. And so I can't access the image via terminal on mac and I can't install Gnome because the net doesn't work.

So anyways, all I wanted to do is to get the files for the website and the mysql file. Though it's turning into a real nightmare now.
Could someone please help me. I would really appreciate it.

---

### Post by dcstar on 2008-09-28
> **Matsta said:**
> Hi there,
So first off I'm a Mac guy and my command line knowledge is virtually next to nothing apart from the absolute basics.
Anyway I'm working on a clients website and I need to upload the files to our server. The clients IT man has set up a VMware image from [http://www.thoughtpolice.co.uk/vmware/](http://www.thoughtpolice.co.uk/vmware/) (Ubuntu server 8.0.4). Now he had set it up on the clients computer that when they click a shortcut, VMware player would launch (the client is using XP) and then you could access the website via a physical local ip address. Now when I got the image, it was in a saved state and ifconfig was running which showed that there was a ethernet connection. When I restarted the VM, and did ifconfig the ethernet connection disappeared. So now it can't access the net at all :(. And so I can't access the image via terminal on mac and I can't install Gnome because the net doesn't work.

So anyways, all I wanted to do is to get the files for the website and the mysql file. Though it's turning into a real nightmare now.
Could someone please help me. I would really appreciate it.

Either reconfigure the VM's network (before you start it) in VMWare, and then go into the VM and make sure that it is set to use an IP address in the environment you are now using it in.

Or, just use USB devices to copy the data off (or on).

---

