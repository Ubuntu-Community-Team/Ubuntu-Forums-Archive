---
title: "Wubi install linux noob issues"
date: 2011-02-06
forum: Hardware
---

### Post by mrjingo on 2011-02-06
Hi,
I'm having issues and hopefully I've not double posted - I'm not a big forum poster but try to read as many articles as I can if I'm having issues rather than bother people, so sorry if this exists somewhere else. (I know that's a bug bear of some highly strung folk :lolflag:)

Ok brand new to linux, experienced windoze user.

Used the wubi installer in win 7 64, on a Sony vaio F series with 1080p display. All installs fine but when booting into ubuntu, display is wrong size for screen and no option for 1080p. Forums suggest I need to edit my xorg.conf file. As I had no access to bottom half of the screen, made a new folder on desktop and browsed to where I read it should be - /etc/x11/xorg.conf - not there. Showed hidden files, still not there. Did a search for it and showed up in another location under an 'example' folder so not even sure if I got the right copy of this file. Gpu is a nvidia 330m. Next issue came as the file in question appeard locked to the user I specified when using the wubi installer. Ok so tried su at a terminal but seems there is no such user. So I can't edit this file. Then at the top of the screen noticed a menu and item for 'additional drivers' - this suggested I use the recommended nvidia driver which it downloaded and told me I needed to restart to activate. Restarted and now I get a black screen and can't even log in.

I'm seeing the funny side but it's a bit of a pain as I wanted to try something new on my comp other than windows :p

<rant>I know there's a lot of different hardware to support and distributions with different software, but surely it's not meant to be this difficult? It'll have to become a whole lot simpler to get more windows users converted IMO</rant>

Anyway appreciate any help :)

---

### Post by mrjingo on 2011-02-06
Anyone? :)

---

### Post by Josunik on 2011-02-06
hello

Do you receive any messages upon starting of Ubuntu, like ubuntu will start on low resolution mode?

---

### Post by mrjingo on 2011-02-07
> **Josunik said:**
> hello

Do you receive any messages upon starting of Ubuntu, like ubuntu will start on low resolution mode?

hi,

the only thing I get after choosing the generic ubuntu option 1 is a very brief message saying 'thermal reporting for required devices not enabled, aborting'

That's since the recommended driver upgrade.

---

