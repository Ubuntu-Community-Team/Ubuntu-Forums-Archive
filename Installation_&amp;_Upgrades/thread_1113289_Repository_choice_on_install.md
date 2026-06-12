---
title: "Repository choice on install"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by EeRr on 2009-04-01
When installing K/Ubuntu, no choice is given to pick and/or manually enter a repository/source address. Is this normal for this distro?

Having a bandwidth limit on my Internet connection, I would rather use the freezone of my ISP ([http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/)) when installing.

The Kubuntu and Ubuntu installs are the first I've come across that offer very few customising choices on install. Is this lack of customising to make it easier for Microsoft users, or just the Ubuntu way?

1. Is there a way to enter different repository addresses on install?

2. If not, will the option ever be included in future releases?

---

### Post by ajgreeny on 2009-04-01
> The Kubuntu and Ubuntu installs are the first I've come across that offer very few customising choices on install. Is this lack of customising to make it easier for Microsoft users, or just the Ubuntu way?It's the ubuntu way.  Don't forget you only have a live CD normally, not a DVD to use for the install so ubuntu picks a smaller range of default apps for the install and makes it simple so as not to baffle installers with a lot of options.  If you want to have options at install, download the Minimal Install CD and then at the time you install you can choose whatever you want, though you will need to know exactly what you really do want to add to the OS to use that successfully, as there's no choices offered by the installer other than the repository you use..

Just go with the normal install with the live CD and you can then add whatever you choose after you're up and running.

---

### Post by mcduck on 2009-04-01
> **EeRr said:**
> 

1. Is there a way to enter different repository addresses on install?

2. If not, will the option ever be included in future releases?
1. No, there isn't. Most new users would newer know what that option is, or what to do with it.

2. Highly unlikely.

If you are worried about your bandwidth limits during the install then remove the network cable when installing, and after installation change the repository to whatever you want before connecting to network and updating the system. (You can change the repository either with a GUI in System/Administration/Software Sources, or by editing /etc/apt/sources.list)

If you do the install from a live-CD changing the repository before starting the installer might work, but I think the installer tries to automatically detect fastest repository for you during the install which would probably make this useless.

---

