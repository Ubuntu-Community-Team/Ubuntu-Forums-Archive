---
title: "Looking for a light-weight linux for USB stick."
date: 2008-10-27
forum: General Help
---

### Post by Suilenroc on 2008-10-27
Hey all. Sorry if this post doesn't exactly belong here, but I couldn't think of anyplace different to place it. 

I'm looking for a lightweight, quick loading, and mediocre-featured distro that works on a USB stick with minimal fuss. 

I have a 4GB USB with Xubuntu on it currently, but it takes forever to boot on this computer. Strangely enough, it boots quickly on this low end laptop that I also own.

I then tried Damn Small Linux on another USB stick, but it was too lightweight for me. I'm looking for something that has just the most basic tools, like a freshly made gentoo install. 

I used to love gentoo because I could install the system, get XORG working, then install XFCE, and I'd have a super light super fast install, which I could then customize to my needs. Does anyone have any idea how I could do something like that for a USB?

Thanks!

---

### Post by earthpigg on 2008-10-27
puppy! :)

---

### Post by Azure.Rise on 2008-10-27
Why would you want something that's mediocore? Go to [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) it has a large repository of tutorials on getting many different distros to run from a flash drive. It has a Gentoo tutorial, but it's for the 2007 release. I don't know if it'll work with 2008.

---

### Post by thestig_992 on 2008-10-27
I have one with that sites own pendrivelinux, which is mandriva, slightly moddified, and looks very similar to windows.

---

### Post by Suilenroc on 2008-10-27
> **Azure.Rise said:**
> Why would you want something that's mediocore? Go to [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) it has a large repository of tutorials on getting many different distros to run from a flash drive. It has a Gentoo tutorial, but it's for the 2007 release. I don't know if it'll work with 2008.

I say that because anything with too many features will just bog it down. Remember, I only have 4 GB of space to work with here, not exactly a lot. So I want something that's at the bare minimum of features, which I can add on to myself with some sort of package download.

---

### Post by Suilenroc on 2008-10-27
Well, Luck me. Lifehacker is doing a special today, Battle of the Thumb Drive linux distros. God I love those guys.

---

### Post by C.S.Cameron on 2008-10-27
Ubuntu and Xubuntu 8.04 and 8.10 if installed using liveusb or usb-creator as persistent start off at less than 700M.
This leaves quite a bit of space for home-rw on a 4G drive.
I find that a 4G is not too bad for a full install either.

---

### Post by hyper_ch on 2008-10-27
DamnSmallLinux

---

### Post by Azure.Rise on 2008-10-27
> **Suilenroc said:**
> I say that because anything with too many features will just bog it down. Remember, I only have 4 GB of space to work with here, not exactly a lot. So I want something that's at the bare minimum of features, which I can add on to myself with some sort of package download.
I think you meant more of a bare bones setup. Mediocre means crappy quality. I had a 700mb Knoppix install on my 1gig flash drive that ran perfectly with Beryl activated. You should be perfectly fine with a full distro. If you want something pretty stripped down and easily customizable go for SLAX. It's a very small Slackware based distro. Installing packages is as simple as downloading the program file of the site and placing it in the programs folder.

---

### Post by alienprdkt on 2008-10-27
> **Suilenroc said:**
> Hey all. Sorry if this post doesn't exactly belong here, but I couldn't think of anyplace different to place it. 

I'm looking for a lightweight, quick loading, and mediocre-featured distro that works on a USB stick with minimal fuss. 

I have a 4GB USB with Xubuntu on it currently, but it takes forever to boot on this computer. Strangely enough, it boots quickly on this low end laptop that I also own.

I then tried Damn Small Linux on another USB stick, but it was too lightweight for me. I'm looking for something that has just the most basic tools, like a freshly made gentoo install. 

I used to love gentoo because I could install the system, get XORG working, then install XFCE, and I'd have a super light super fast install, which I could then customize to my needs. Does anyone have any idea how I could do something like that for a USB?

Thanks!

Well if you like gentoo why not put the gentoo live cd or minimal install (or copy live cd then configure GRUB to choose your boot) on a usb stick, as I did? 
[http://www.gentoo.org/doc/en/liveusb.xml](http://www.gentoo.org/doc/en/liveusb.xml)

---

### Post by snowpine on 2008-10-27
Definitely check out SliTaz; it has a very nice LiveUSB tool called tazusb!

edit: there are Stable and Cooking versions; I recommend Cooking as I much prefer Openbox+PCmanfm

---

### Post by Suilenroc on 2008-10-29
> **snowpine said:**
> Definitely check out SliTaz; it has a very nice LiveUSB tool called tazusb!

edit: there are Stable and Cooking versions; I recommend Cooking as I much prefer Openbox+PCmanfm

Gonna give it a try now, thanks! This one may be perfect, I like the customizabitily plus the low memory footprint. The computers that I'm using this on suck massively, some only have 128MB of RAM.

---

### Post by snowpine on 2008-10-29
> **Suilenroc said:**
> Gonna give it a try now, thanks! This one may be perfect, I like the customizabitily plus the low memory footprint. The computers that I'm using this on suck massively, some only have 128MB of RAM.

For 128mb of ram, I recommend SliTaz stable or loram. Cooking seems to perform better with 160mb or more, if you want to use Firefox. This is just one person's experience. :)

---

### Post by Suilenroc on 2008-10-29
I've tried slitaz now on the computers that I need it on, and it's alright. However, there's a crippling problem: No internet. The ethernet is plugged in, but I can't get the internet.

Also, it has be reinstall X.org and Vesa every time I use it, and that adds about a minute to the boot time. I'm gonna keep looking...My ideal distro would be this:

An XFCE window manager base. It's lightweight enough that I think a 128MB RAM computer could handle it, but not so lightweight that it's annoying to use. 

Ability to install a variety of packages. Firefox, AbiWord, and others as the need comes along.

---

### Post by snowpine on 2008-10-29
> **Suilenroc said:**
> I've tried slitaz now on the computers that I need it on, and it's alright. However, there's a crippling problem: No internet. The ethernet is plugged in, but I can't get the internet.

Also, it has be reinstall X.org and Vesa every time I use it, and that adds about a minute to the boot time. I'm gonna keep looking...My ideal distro would be this:

An XFCE window manager base. It's lightweight enough that I think a 128MB RAM computer could handle it, but not so lightweight that it's annoying to use. 

Ability to install a variety of packages. Firefox, AbiWord, and others as the need comes along.

Very few live distros do well with only 128mb of ram (Puppy, DSL, etc). Most live environments fare better with 256mb or more. However, in my experience, most computers that are old enough to only have 128mb of ram also have old BIOS that can't boot from a USB stick. So it may not be an issue. :)

---

### Post by Suilenroc on 2008-10-29
Alrighty, I could be mistaken on the RAM. I know the some of the computers have 512 MB, and some have less. Based on the slowness when running XP, I thought it was 128, but it could be 256.

---

