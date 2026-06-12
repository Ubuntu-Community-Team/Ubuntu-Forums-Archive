---
title: "Microsoftising Linux?"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by joelgsf on 2009-08-07
Hi! I'm an old Thunderbird user and not even slightly have ever thought of using Evolution. One of my first actions after installing Ubuntu was trying to remove it (Evolution) to install Thunderbird. I was surprised as how intricated it is with several other applications, and ended up leaving several of its libraries and tools installed, fearing to damage severely the functionality of my system. Does it has to be so? Isn't this a kind of "Microsoftising" Linux?

---

### Post by snowpine on 2009-08-07
Ubuntu is a Linux "distribution," which means it is not just an operating system, but also a full suite of applications so it is ready-to-use for most everyday tasks. If you disagree with the developers' choice of what to include, you have a couple of options: one is to perform a minimal install with only the applications you choose ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)), another is to simply not use Evolution and remove the icon from your panel. :)

ps the non-sarcastic answer is that evolution is tightly integrated with the Gnome desktop, and removing it will also remove ubuntu-desktop, which will probably remove a lot of other stuff you want to keep. :( I personally prefer an approach such as Arch, where you have fine-grained control over that sort of thing.

---

### Post by joelgsf on 2009-08-08
I understand your point snowpine. This is the Ubuntu distribution, and I am loving it. I just think that tying (Can I say so? Sorry but I'm not a native English speaker) the desktop to an e-mail package doesn't make much sense. Certainly there were good reasons to do so, but I can't imagine what these reasons were.
My first action, actually, was to remove the Icon from the toolbar, and after I went on removing all that seemed not to interfere with those precious stuff you mention. As I am not a suicidal, I did it within a VM, just in case ;).
I'm going to look into the link you pointed out. I will certainly learn more about Ubuntu/Linux from there.
Thank you for your attention.

---

### Post by snowpine on 2009-08-08
No argument from me. ;) Tying the browser to the operating system is the reason Microsoft got sued in Europe, right?

ps Your English is very good. :)

---

### Post by Mark Phelps on 2009-08-08
> **joelgsf said:**
> Isn't this a kind of "Microsoftising" Linux?

Well ... no.  

Including a set of useful applications by default is what nearly every OS distribution does.  The idea is to provide the user with a working system once the OS installation is done.  A bare OS with nothing but an empty desktop (which you CAN get with some Linux distros) is not very useful to most folks.

Now, if we were to FORCE a particular browser on everyone, and then integrate it into the OS such that removing it broke the OS, that would be much more along the line of "Microsoftising".  Course, we'd have to figure out a way to charge you $200 USD for an OS "upgrade" as well ...

---

### Post by joelgsf on 2009-08-10
> Quoting Phelps:
"Including a set of useful applications by default is what nearly every OS distribution does. The idea is to provide the user with a working system once the OS installation is done. A bare OS with nothing but an empty desktop (which you CAN get with some Linux distros) is not very useful to most folks."

Anyone will agree with what you say, Phelps. But "a set of useful applications" is not the same as _a set of useful applications around a single application_, with links that cannot be broken. This is what I see with respect to Evolution in Ubuntu. Please correct me if I'm seeing it wrongly. All that I would like to have is beeing able to keep everything, except Evolution and its accessories (like agenda, etc.).

---

### Post by Wiebelhaus on 2009-08-10
It's a ["Metapackage"]("https://help.ubuntu.com/community/MetaPackages") of Gnome-Desktop.

---

### Post by slakkie on 2009-08-10
It is perfectly safe to remove evolution from your machine:

```

aptitude -s remove evolution
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  evolution-exchange evolution-plugins
The following packages have been automatically kept back:
  k3b
The following packages will be REMOVED:
  evolution
0 packages upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 8544kB will be freed.
The following packages have unmet dependencies:
  evolution-exchange: Depends: evolution (>= 2.22.3.1) but it is not installable
  evolution-plugins: Depends: evolution (>= 2.22.3.1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
contact-lookup-applet
evolution-exchange
evolution-plugins
nautilus-sendto
ubuntu-desktop

Leave the following dependencies unresolved:
evolution-common recommends evolution
Score is -165

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
contact-lookup-applet
evolution-exchange
evolution-plugins
ubuntu-desktop

Downgrade the following packages:
nautilus-sendto [0.13.2-0ubuntu3 (hardy-updates, now) -> 0.13.2-0ubuntu1 (hardy)]

Leave the following dependencies unresolved:
nautilus-sendto recommends evolution (>= 2.4)
evolution-common recommends evolution
Score is -404

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  k3b
The following packages will be automatically REMOVED:
  contact-lookup-applet evolution-exchange evolution-plugins ubuntu-desktop
The following packages will be DOWNGRADED:
  nautilus-sendto
The following packages will be REMOVED:
  contact-lookup-applet evolution evolution-exchange evolution-plugins ubuntu-desktop
0 packages upgraded, 0 newly installed, 1 downgraded, 5 to remove and 11 not upgraded.
Need to get 55.5kB of archives. After unpacking 13.4MB will be freed.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```

---

### Post by joelgsf on 2009-08-15
Slakkie, as far as I can see in your procedure I will end up without a desktop. I have removed Evolution leaving behind all packages that would mess with other applications using the "Systems --> Administration --> Synaptic Package Manager". I believe that's the best I can do, though it is not what I would like the  most.

---

### Post by hansdown on 2009-08-15
You are correct, and most wise, (if I may say) joelgsf.

There are some dependencies in ubuntu. You can add what you like to use.

Some things are better left intact.

---

### Post by Jeffery Mewtamer on 2009-08-16
Like joelgsf, I dislike the default software bundle included with Ubuntu and its variants. As such, I install kde-minimal(previously kde-core) on top of a server installation to give me a basic, yet stable Desktop to work with.

The gnome-core metapackage should provide a bare bones Gnome Desktop that would allow you to strip out all of the unwanted bundled software without destabilizing your system, though starting from a server installation would provide a cleaner set-up with less time spent removing unwanted packages.

---

### Post by meindian523 on 2009-08-16
+1.Evolution is far too integrated with many other applications.You can remove evolution,but try to remove anything that mentions evolution from Synaptic and you end up losing a lot of desired applications.


And @OP,removing ubuntu-desktop doesn't leave you without a desktop,it's just a meta package which ensures that all the elements required for a Ubuntu GNOME DE are pulled in when you install it,by assigning them dependency status.Similarly,if you install kubuntu-desktop,you will get a complete KDE DE,but removing kubuntu-desktop doesn't leave you without KDE.

---

### Post by slakkie on 2009-08-16
> **joelgsf said:**
> Slakkie, as far as I can see in your procedure I will end up without a desktop. I have removed Evolution leaving behind all packages that would mess with other applications using the "Systems --> Administration --> Synaptic Package Manager". I believe that's the best I can do, though it is not what I would like the  most.

No you won't. You will remove the meta-package, which is fine.

---

