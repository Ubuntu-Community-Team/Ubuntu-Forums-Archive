---
title: "Removing linux from system."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by sb360 on 2009-04-25
I'm looking to remove ubuntu from my system (with a view to installing a different distro), How would I go about this so as not to endanger my windows install. Unfortunately I never had a windows disk as it came preloaded on my computer.

Also is there any distro you would particularly recommend for a total newbie, I have had sabayan suggested to me by a friend and I am going to try that, if only from a live disk at first, is there anything else I should look into before making my choice ?

Thanks in advance

---

### Post by briandu on 2009-04-25
cant imagine why you want to remove this from your PC.

However you have not stated the config so since there are many ways to do this how can we help you?

Is it XP first that Linux or is it Linux or how is it laid out?

---

### Post by sb360 on 2009-04-25
Sorry, I can tell you that I installed 9.04 from a live cd and that in my boot menu ubuntu is above windows (vista rather than XP though).

And what output do you want me to post ? 

As for why I want to remove it I feel that I should have looked around and got some more advice before jumping in and after doing so I have decided to try another distro, I just want to see what some others have to offer rather than limiting myself just to u/xu/ku buntu.

---

### Post by coffeecat on 2009-04-25
I should imagine you have just two Linux partitions, the root partition and a swap partition. With any of the major distros, the installer will give you a 'manual' or 'advanced' option when you get to the partitioning stage. All you have to do is to tell it to use your present root and swap partitions for root and swap, and it will reformat the root partition, install the distro and set up a new grub bootloader for you, booting into the new distro or Windows. However, different distros use different installers and they vary in their newcomer friendliness.

As far as recommending distros for newbies, I'm not sure I would go for Sabayon. It's very slick and shiny at first but it has a reputation for breaking after several upgrades. I'm only going on hearsay, mind. Others may have good experiences.

What I would recommend is in this order, with some comments.

Linux Mint - based on Ubuntu with a minty facelift. Even more newcomer friendly than Ubuntu, but you may be wanting to try something quite different from Ubuntu.

Mandriva - Mandriva went through a bad patch a couple of years ago, but bounced back in 2008. Their 2008.1 and 2009.0 versions were very good. They probably have the most friendly installer going. Wait a couple of weeks and the new 2009.1 version should be released. I would definitely think of giving this a go. You will be able to get live CD installers in two versions: gnome and kde desktop.

Mepis - Nice distro using the older KDE 3.5 desktop.

openSUSE - An excellent distro - worth a try.

Fedora - Not really one to recommend to newbies for a couple of reasons: its target user base is really experienced enthusiasts and it can be too bleeding edge for some people's liking. Also, with its strict open-source policy, getting proprietary drivers and codecs working is more of a fiddle than with Ubuntu. Having said that, it's well worth looking at some time. For getting the proprietary stuff working [bookmark this page]("http://www.mjmwired.net/resources/mjm-fedora-f10.html") for when and if you decide to give it a try.

---

### Post by autocrosser on 2009-04-25
I would just install another harddrive so you can compare side-by-side--I have worked with Ubuntu from the very first & have looked at several other distros over the years (I have a Fedora11 install on one of my drives right now)--I think after weighing the pros & cons you will come back to Ubuntu...It works well.

---

### Post by sb360 on 2009-04-25
> **autocrosser said:**
> I would just install another harddrive so you can compare side-by-side--I have worked with Ubuntu from the very first & have looked at several other distros over the years (I have a Fedora11 install on one of my drives right now)--I think after weighing the pros & cons you will come back to Ubuntu...It works well.

IU would if I could, but I cant install another harddrive as this is a laptop, hopefully in the near future I will build my own computer and then can try many different distros.

> **coffeecat said:**
> I should imagine you have just two Linux partitions, the root partition and a swap partition. With any of the major distros, the installer will give you a 'manual' or 'advanced' option when you get to the partitioning stage. All you have to do is to tell it to use your present root and swap partitions for root and swap, and it will reformat the root partition, install the distro and set up a new grub bootloader for you, booting into the new distro or Windows. However, different distros use different installers and they vary in their newcomer friendliness.

As far as recommending distros for newbies, I'm not sure I would go for Sabayon. It's very slick and shiny at first but it has a reputation for breaking after several upgrades. I'm only going on hearsay, mind. Others may have good experiences.

What I would recommend is in this order, with some comments.

Linux Mint - based on Ubuntu with a minty facelift. Even more newcomer friendly than Ubuntu, but you may be wanting to try something quite different from Ubuntu.

Mandriva - Mandriva went through a bad patch a couple of years ago, but bounced back in 2008. Their 2008.1 and 2009.0 versions were very good. They probably have the most friendly installer going. Wait a couple of weeks and the new 2009.1 version should be released. I would definitely think of giving this a go. You will be able to get live CD installers in two versions: gnome and kde desktop.

Mepis - Nice distro using the older KDE 3.5 desktop.

openSUSE - An excellent distro - worth a try.

Fedora - Not really one to recommend to newbies for a couple of reasons: its target user base is really experienced enthusiasts and it can be too bleeding edge for some people's liking. Also, with its strict open-source policy, getting proprietary drivers and codecs working is more of a fiddle than with Ubuntu. Having said that, it's well worth looking at some time. For getting the proprietary stuff working [bookmark this page]("http://www.mjmwired.net/resources/mjm-fedora-f10.html") for when and if you decide to give it a try.

Thanks for the advice, the linux mint looks very interesting and I think I will try that as well. Will all installers have the ability to use my current partitions then or will it just be certain installers.

---

### Post by balaknair on 2009-04-25
If you're looking for something easy, try PCLinuxOS Gnome Edition. It's pretty, easy, and comes with pretty much everything you need(Flash, mp3 and DVD playback) enabled out of the box.

The only hiccup is that partitioning isn't as easy and intuitive as with Ubuntu. Otherwise it's a great distro for newbies.

Pretty much all installers have the ability to use your current partitions, it's just that GUI for these might differ.

Try taking this excellent quiz(Linux Distro Chooser) to help you decide and learn more about your options
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

### Post by coffeecat on 2009-04-25
> **sb360 said:**
> Will all installers have the ability to use my current partitions then or will it just be certain installers.

As far as I remember all will be able to do just that, but they do vary in their user-friendliness. If you understand partitions, you should be fine. By the way, I forgot to mention that the latest Mint (Mint 6) is based on Ubuntu 8.10. Mint 7, to be based on 9.04, won't be out for a month or so. Since you're running a laptop, this might be an issue since 9.04 will have better hardware support (mostly) than 8.10. The best thing would be to download the live CD and see how well it detects your hardware. The wireless card is often the critical thing here.

In fact, if you've got plenty of download allowance (assuming you've got broadband), why not download the live CDs for all the distros I listed? Run them all live, see how well they detect your hardware and see which you like best before committing yourself to a hard drive install.

---

### Post by sb360 on 2009-04-25
> **coffeecat said:**
> As far as I remember all will be able to do just that, but they do vary in their user-friendliness. If you understand partitions, you should be fine. By the way, I forgot to mention that the latest Mint (Mint 6) is based on Ubuntu 8.10. Mint 7, to be based on 9.04, won't be out for a month or so. Since you're running a laptop, this might be an issue since 9.04 will have better hardware support (mostly) than 8.10. The best thing would be to download the live CD and see how well it detects your hardware. The wireless card is often the critical thing here.

In fact, if you've got plenty of download allowance (assuming you've got broadband), why not download the live CDs for all the distros I listed? Run them all live, see how well they detect your hardware and see which you like best before committing yourself to a hard drive install.

Yea when I was running 8.10 The only problem I did have was with the wireless, I will try all of them and the sabayon live CD that I have made then. Also are xubuntu or kubuntu much different from ubuntu or is there not any point trying them ?

---

### Post by coffeecat on 2009-04-25
> **sb360 said:**
> Also are xubuntu or kubuntu much different from ubuntu or is there not any point trying them ?

They have the same underlying structure but the desktops are different. Xfce for Xubuntu and KDE for Kubuntu. The different desktops can be quite markedly different. If you're new to Linux the transition from Gnome to KDE or vice versa can seem almost like the transition from one OS to another. With KDE you have the added complication of the 3.* series and the newer 4.* series which is a radical change. Kubuntu 9.04 comes with KDE 4.2.

**Edit:** thinking about this a bit more, I would suggest going for a different distro but with the Gnome desktop. Say Mandriva or PCLinuxOS as balaknair suggested and which I forgot about. Or go for Kubuntu 9.04. That way you're only changing one thing - underlying distro or desktop, so there will be some familiarity around. If you go for Kubuntu 9.04, I'd suggest doing a bit of googling and searching for KDE 4.2 to read about it. It can be a bit of a challenge if you're not used to it.

**Second edit:** another idea. :wink: If you're interested in trying Kubuntu 9.04, just open Synaptic and install 'kubuntu-desktop'. Then you get a choice of desktop at the login screen. That might be worth trying before you distro hop.

---

### Post by sb360 on 2009-04-25
The distro chooser quiz didnt come up with anything you guys havent already mentioned, opensuse, kubuntu, linux mint, mandriva and ubuntu all at 100% with fedora, mepis and pclinuxos at 90%.

You guys are good, and I am now torrenting all of these I think (bar ubuntu) and will try them all in due course. 

Thanks for all the help and advice.

---

### Post by DracoJesi on 2009-04-25
> **sb360 said:**
> I'm looking to remove ubuntu from my system (with a view to installing a different distro), How would I go about this so as not to endanger my windows install. Unfortunately I never had a windows disk as it came preloaded on my computer.

Also is there any distro you would particularly recommend for a total newbie, I have had sabayan suggested to me by a friend and I am going to try that, if only from a live disk at first, is there anything else I should look into before making my choice ?

Thanks in advance

hmm, as a note here, Ubuntu is very user friendly when it comes to being a newbie, I've never used Sabayan, but I think you'd be hard pressed to find with a smaller learning curve...

---

### Post by autocrosser on 2009-04-25
Another thought would be to use a external drive for testing use---It's a bit "fun" to setup, but allows you to install what you want & nuke it if you don't like it :):)

---

### Post by sb360 on 2009-04-26
> **autocrosser said:**
> Another thought would be to use a external drive for testing use---It's a bit "fun" to setup, but allows you to install what you want & nuke it if you don't like it :):)

Yea I was considering that but I had heard that it was a bit tricky, and I don't have a drive that isn't used for backups.

> **DracoJesi said:**
> hmm, as a note here, Ubuntu is very user friendly when it comes to being a newbie, I've never used Sabayan, but I think you'd be hard pressed to find with a smaller learning curve...

I have heard that as well but I am not doing this solely because of user friendliness, It is also to try something new and to get a better idea of what is available.

---

