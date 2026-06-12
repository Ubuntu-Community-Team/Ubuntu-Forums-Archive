---
title: "[SOLVED] Which one?"
date: 2008-10-28
forum: General Help
---

### Post by Yezinki on 2008-10-28
Hi there,

Out of the 2 Kubuntu 8.04 & Kubuntu 8.04 KDE4 Remix. which one should I download & install or can I install both versions?

Their major differences, pros & cons?

Hoping to hear as always!

Regards!

---

### Post by Yezinki on 2008-10-28
Are they both similar to Ubuntu Hardy Heron 8.04 LTS...........I understand  the difference of Genome & KDE interface!

---

### Post by AlanR8 on 2008-10-28
The Remix comes with KDE4 as standard (I think)and 8.04 comes with KDE 3.*.* as standard.

I'm a Kubuntu user and have 8.04 installed with KDE4 installed as well as 3.*.*. It all works well.

That said, I've not booted into 3.*.* for about three weeks now, no need.

I installed Kubuntu 8.10 on my play machine, EeePC, and that works well.

Pure KDE4, cutting edge stuff and no safety net.

Love it!

---

### Post by Yezinki on 2008-10-28
Thanks,

Do you have separate loaders for both or have upgraded the 8.04 with KDE3 to KDE 4 using Synaptic?

What I mean is it a dual boot or a single?

Regards!

Yezinki.

---

### Post by Yezinki on 2008-10-28
> **AlanR8 said:**
> The Remix comes with KDE4 as standard (I think)and 8.04 comes with KDE 3.*.* as standard.

I'm a Kubuntu user and have 8.04 installed with KDE4 installed as well as 3.*.*. It all works well.

That said, I've not booted into 3.*.* for about three weeks now, no need.

I installed Kubuntu 8.10 on my play machine, EeePC, and that works well.

Pure KDE4, cutting edge stuff and no safety net.

Love it!


What exactly do you mean by NO SAFETY??

---

### Post by rvportugal on 2008-10-28
I've been running Kubuntu 8.10 with KDE4 on a Dell XPS and it is lovely! Now it is on Release Candidate, so why not to give a try?

---

### Post by Yezinki on 2008-10-28
I plan using it on my Sony Vaio, running Vista on my XPS 1730!

---

### Post by SuperSonic4 on 2008-10-28
> **Yezinki said:**
> Thanks,

Do you have separate loaders for both or have upgraded the 8.04 with KDE3 to KDE 4 using Synaptic?

What I mean is it a dual boot or a single?

Regards!

Yezinki.

you may install KDE4 remix from KDE by the following command. Replace core with desktop for the full KDE4 desktop (I prefer the core apps).

```
sudo aptitude install kubuntu-kde4-core
```

You will be able to choose either one from the login menu under the session icon so from grub it will be a single boot.

That said you can always do a dual boot with KDE and KDE4 remix on seperate partitions by burning the ISO files and installing as normal. This would be a dual boot

---

### Post by Yezinki on 2008-10-28
> **SuperSonic4 said:**
> you may install KDE4 remix from KDE by the following command. Replace core with desktop for the full KDE4 desktop (I prefer the core apps).

```
sudo aptitude install kubuntu-kde4-core
```

You will be able to choose either one from the login menu under the session icon so from grub it will be a single boot.

That said you can always do a dual boot with KDE and KDE4 remix on seperate partitions by burning the ISO files and installing as normal. This would be a dual boot


Since  you prefer the core apps..........how do you run both?

---

### Post by SuperSonic4 on 2008-10-28
You can install the KDE4 desktop by ```
sudo aptitude install kubuntu-kde4-desktop
```

is that what you meant?

---

### Post by Yezinki on 2008-10-28
What I mean is that can one install both on a single drive?

---

### Post by Yezinki on 2008-10-28
For installing both does one have to download both the ISOs?

---

### Post by Yezinki on 2008-10-28
> **SuperSonic4 said:**
> You can install the KDE4 desktop by ```
sudo aptitude install kubuntu-kde4-desktop
```

is that what you meant?

Can one install both complete not simply just the desktop thats what I meant!

Regards!

---

### Post by SuperSonic4 on 2008-10-28
> **Yezinki said:**
> What I mean is that can one install both on a single drive?

Yes, but you have to partition this drive, or if you can have them as different sessions. If you partition it there will be no interaction except through /media.

> **Yezinki said:**
> For installing both does one have to download both the ISOs?

If you want a clean install on two different partitions then yes. If you want them different sessions then no you can use adept and the codes above.

> **Yezinki said:**
> Can one install both complete not simply just the desktop thats what I meant!

Regards!

You can have both installed. the kubuntu-desktop and kubuntu-kde4-desktop packages are a whole OS, complete with GUI, default applications and settings.

---

### Post by AlanR8 on 2008-10-29
My comment about no safety net.....

One thing I have found is KDE4 is still in development piece and the full functionality and customisation that you find in KDE3.*.* is not there yet. That said, there's enough for the average user to have a fully functional desktop that just works.

I also run a Vaio with a Nvidia card and I find the folder view does not work well yet is perfect on my EeePc and the wife's dual boot Dell that has an ATI card.

I understand that KDE4 is getting frequent updates with the next big shift to 4.2 in early new year.

I don't dual boot, there's an option on the login screen to select which version you want to run.

---

### Post by Yezinki on 2008-10-29
Hi there,

Gonna download Intrepid Ibex Kubuntu.

Regards!

---

### Post by AlanR8 on 2008-10-30
Go for it and enjoy!

---

