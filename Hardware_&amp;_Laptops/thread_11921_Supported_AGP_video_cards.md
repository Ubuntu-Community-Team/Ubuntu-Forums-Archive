---
title: "Supported AGP video cards"
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by Sham on 2005-01-20
Hi all,

I have been trying in vain to get a matrox parhelia AGP card working in a Dell workstation for the past 2 days. All relevent threads havn't helped. I can install Ubuntu (warty), but X will not start (even using the vesa driver).

It seems support for this card is very bad, so my question is this:

which card should I get? I would be looking for at least 128mb. It seems the nvidia chipset is well supported. Should i go for this? 

On the off-chance, if anyone knows how to get a matrox parhelia working then please let me/us know. 

Cheers

---

### Post by Viro on 2005-01-20
[QUOTE=Sham]Hi all,

I have been trying in vain to get a matrox parhelia AGP card working in a Dell workstation for the past 2 days. All relevent threads havn't helped. I can install Ubuntu (warty), but X will not start (even using the vesa driver).

It seems support for this card is very bad, so my question is this:

which card should I get? I would be looking for at least 128mb. It seems the nvidia chipset is well supported. Should i go for this? 

On the off-chance, if anyone knows how to get a matrox parhelia working then please let me/us know. 

Cheers[/QUOTE]
 Tried the suggestions on this page yet? [http://www.sowerbutts.com/matrox/](http://www.sowerbutts.com/matrox/)

---

### Post by Sham on 2005-01-20
I didn't even see that page, butI'm unsure about how to aply a patch. Web guides say dump the patch in /usr/src/linux but what I have in /usr/src is:

$ ls
kernel-kbuild-2.6-3          linux-headers-2.6.8.1-4
linux-headers-2.6.8.1-3      linux-headers-2.6.8.1-4-386
linux-headers-2.6.8.1-3-386  rpm


Can you tell me where I place the patch?

---

### Post by Viro on 2005-01-20
[QUOTE=Sham]I didn't even see that page, butI'm unsure about how to aply a patch. Web guides say dump the patch in /usr/src/linux but what I have in /usr/src is:

$ ls
kernel-kbuild-2.6-3          linux-headers-2.6.8.1-4
linux-headers-2.6.8.1-3      linux-headers-2.6.8.1-4-386
linux-headers-2.6.8.1-3-386  rpm


Can you tell me where I place the patch?[/QUOTE]
 You need to download the corresponding Linux source for your kernel. In the terminal (or Synaptic Package Manager) search for linux-source. Download the one that corresponds to your installed kernel, in this case 2.6.8.1-3.

Once installed, go to /usr/src/ and uncompress the archive file that was downloaded, something like linux-source-2.6.8.1-3.tar.bz2. Use the following command to uncompress the archive.
```

sudo tar -xvjf linux-source-2.6.8.1-3.tar.bz2
```

This will create a folder linux-source-2.6.8.1-3. You place the patches in there.

---

