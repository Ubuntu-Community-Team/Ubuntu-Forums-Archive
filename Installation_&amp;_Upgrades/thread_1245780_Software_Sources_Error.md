---
title: "Software Sources Error"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by georgena on 2009-08-20
Hello All,

I sure hope that you can help. I am getting the following error when I try to reload my software sources in Synaptic.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE

As a little background let me tell you that I installed the Ubuntu One client the day before yesterday and last night I was trying to install XBMC via the XBMC site instructions which detailed adding the source and importing the GPG key. I think that this may be where things went wrong. I did however remove the XBMC source and it's key (or so I thought) last night. I did finally find another way to get XBMC installed via the community Ubuntu pages but this warning continues to come up. I am not sure if this has to do with Ubuntu One or not though since this was also a recent addition. Any ideas? Thanks in advance for any help you can provide.

George

---

### Post by running_rabbit07 on 2009-08-20
> **georgena said:**
>  I did however remove the XBMC source and it's key (or so I thought) last night. 

Go to System>Administration>Software Sources and see if that one is gone. Or at least not ticked. If it is ticked, untick it.

Of coarse that probably isn't the fix. Was worth a try though.

---

### Post by georgena on 2009-08-20
> **running_rabbit07 said:**
> Go to System>Administration>Software Sources and see if that one is gone. Or at least not ticked. If it is ticked, untick it.

Of coarse that probably isn't the fix. Was worth a try though.


Duh, I never thought to try unchecking them one at a time the XBMC source had no effect when I unchecked it but this one did

[http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu)

Any ideas as to what source this is pointing to?

---

### Post by running_rabbit07 on 2009-08-20
> **georgena said:**
> Duh, I never thought to try unchecking them one at a time the XBMC source had no effect when I unchecked it but this one did

[http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu)

Any ideas as to what source this is pointing to?

I am not sure what program that would be for. Do you remember adding it to install something? I have one like that but it has openoffice where your's has bisigi.

If it is just giving you an error, it should still be completing the updates when you do them.

Honestly, I would just disable it for now. The Canonical ones are the only ones you really need. If you have an anti-virus like the bitdefender one listed on mine, it will need it's updates.

---

### Post by running_rabbit07 on 2009-08-20
I just did a search and the bisigi one is for a theme you installed. [See it here.]("https://launchpad.net/zgegball-themes")

---

### Post by georgena on 2009-08-21
> **running_rabbit07 said:**
> I just did a search and the bisigi one is for a theme you installed. [See it here.]("https://launchpad.net/zgegball-themes")


Running rabbit you are a lifesaver. I remember installing a few very slick themes from there but that was a few weeks back and nothing had been giving me any issues up until now. That really makes me feel more comfortable knowing what that was for. Thanks again. That means my issue has been resolved

How do I change the subject so that it reads resolved?

George

---

### Post by running_rabbit07 on 2009-08-21
> **georgena said:**
> How do I change the subject so that it reads resolved?

Your Welcome

You can change the title on the top post by clicking to "Edit," then click "Go Advanced", then you can change the title. It will not change the thread title though.

---

### Post by donpedrodos on 2009-08-21
Try this in the Terminal:```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
```

---

