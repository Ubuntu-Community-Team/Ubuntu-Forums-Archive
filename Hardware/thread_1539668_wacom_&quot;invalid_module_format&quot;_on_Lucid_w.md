---
title: "wacom &quot;invalid module format&quot; on Lucid with 2.6.35-10-generic-pae"
date: 2010-07-26
forum: Hardware
---

### Post by Thryn on 2010-07-26
Today I updated my kernel (twice...). The second time was to take advantage of new support of my laptop's touchpad. So now I have 2.6.35-10-generic-pae.

I'm used to having to [configure and make linux-wacom]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/") every time I update the kernel. So I went to do so, and it complained, as usual, that I should use xf86-input-wacom, but I ignored it as usual, because it's always worked anyway.

But then my troubles began. Sadly I can't remember every issue I had, but after downloading the latest linuxwacom (0.8.8.7) I got to the point of making and copying wacom.ko as in the tutorial I linked above, and then got the following errors:

```
sudo rmmod wacom
ERROR: Module wacom does not exist in /proc/modules
sudo modprobe wacom
FATAL: Error inserting wacom (/lib/modules/2.6.35-10-generic-pae/kernel/drivers/input/tablet/wacom.ko): Invalid module format

```

And of course my tablet (Bamboo pen) doesn't work at the moment. I restarted, since I figured maybe, just maybe, it would work since I set it up to load on startup. But no.

I've never had this problem before. Any ideas?

---

### Post by Xavier Oddmon on 2010-10-06
[SIZE="1"][COLOR="Red"]Did you ever find a solution to this? I've had to do the same thing to make my wacom bamboo CTL-460 work every time there's a kernel update. As of 2.6.32-25, i'm getting the same error.[/COLOR][/SIZE]

Scratch that. It turns out that there's a repository for this.
```

sudo apt-add-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get update install wacom-dkms

```

After installing this package and plugging in my tablet, all is well. And, you shouldn't have to do it after every kernel update!

---

### Post by ubername on 2010-10-18
> **Xavier Oddmon said:**
> [SIZE="1"][COLOR="Red"]Did you ever find a solution to this? I've had to do the same thing to make my wacom bamboo CTL-460 work every time there's a kernel update. As of 2.6.32-25, i'm getting the same error.[/COLOR][/SIZE]

Scratch that. It turns out that there's a repository for this.
```

sudo apt-add-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get update install wacom-dkms

```

After installing this package and plugging in my tablet, all is well. And, you shouldn't have to do it after every kernel update!

Last line should be 
```
sudo apt-get install wacom-dkms
```

---

