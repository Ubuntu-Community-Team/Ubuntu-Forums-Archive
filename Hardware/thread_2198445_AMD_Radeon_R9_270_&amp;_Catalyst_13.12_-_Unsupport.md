---
title: "AMD Radeon R9 270 &amp; Catalyst 13.12 - Unsupported hardware?"
date: 2014-01-08
forum: Hardware
---

### Post by billy.bloggz on 2014-01-08
I recently bought a Dell XPS 8700 PC with an AMD Radeon HD R9 270 2GB GDDR5 GPU. I've installed the Linux Catalyst 13.12 driver from the [AMD website]("http://support.amd.com/en-us/download/desktop?os=Linux+x86"). After installing it there is now a transparent image stuck at the bottom right of the screen stating "AMD Unsupported Hardware", which is odd because the AMD website clearly [states that Radeon R9 270X is supported]("http://support.amd.com/en-us/kb-articles/Pages/amdcatalyst13-12linreleasenotes.aspx"). Phoronix has also [warmly reviewed]("http://www.phoronix.com/scan.php?page=article&item=amd_radeonr9_270x&num=10") the Radeon R9 270X's performance on Linux, so obviously it is supposed to work. There is also the odd quirk that I cannot run AMD "Catalyst Control Center (Administrator)" from the Application Menu, although for some reason it works if I open it through the terminal. On the information page of the Catalyst Control Center, I notice that the GPU is identified as a Radeon HD8800 Series.

---

### Post by QIII on 2014-01-08
Hello!

The R9s are based on HD 8000s.  AMD was just stuck because if they called them HD 9000s, then the next step would be HD 10000 -- a bit silly.

So the name changed to R9, which sounds like "Wheee!  New!"  But it's not.  

In the past, since AMD started doing the signature thing with their drivers, this meant that the driver installed was not new enough to support the card.  It could be that the signature and the PCI ID of your particular card crossed paths and missed each other between shipment of your card and the publication of the new driver.

If you would, please enter the following in the terminal and post back the results:

```
fglrxinfo
```

---

### Post by billy.bloggz on 2014-01-09
> **QIII said:**
> If you would, please enter the following in the terminal and post back the results:

```
fglrxinfo
```
fglrxinfo brings up:

```
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon(TM) HD8800 Series
OpenGL version string: 4.2.12337 Compatibility Profile Context 13.251
```

---

### Post by Yellow Pasque on 2014-01-09
>  there is now a transparent image stuck at the bottom right of the screen stating "AMD Unsupported Hardware"

It's called a watermark and it happens all the time with really new hardware on Catalyst because of the aforementioned PCI ID issue. Beware hacks that edit binary files. If you use a hack that was made with a different version of Catalyst, you end up with a non-booting system.

The best thing you can do is wait for a newer version of Catalyst. Actually, the best thing is not to buy the latest and greatest AMD GPU because of BS like this, especially if you plan to run a binary driver. (Older generations are good if you want to run the opensource driver.)

---

### Post by billy.bloggz on 2014-01-09
> **Temüjin said:**
> The best thing you can do is wait for a newer version of Catalyst. Actually, the best thing is not to buy the latest and greatest AMD GPU because of BS like this, especially if you plan to run a binary driver. (Older generations are good if you want to run the opensource driver.)I'm not just assuming that Catalyst would work with a recently manufactured GPU. I had heard before that AMD wasn't great with Linux support. I just took it for granted that if the AMD website said that my specific GPU was compatible with the Catalyst driver, then it is presumably currently supported hardware. Is the AMD website unreliable about information on their own drivers or is there some fine distinction between "compatible" & "supported" hardware that I am missing?

As it stands now, I decided I'd give the beta version of Catalyst a try. Now the "unsupported hardware" watermark is gone, I can actually open the Catalyst Control Center from the Application Menu and I see that it now identifies my GPU as a AMD Radeon R9 200 Series. Of course I'd prefer to run a stable version, but if that's off the table for now I guess I will stick with this.

---

### Post by Yellow Pasque on 2014-01-09
Usually, the driver will work okay even with the watermark. The watermark is just AMD's (extremely annoying and pervasive) way of saying, "Don't file bugs because we don't guarantee it will work."

I don't know if CCC not opening from the GUI was related to your specific GPU or not..

---

### Post by wilkins24 on 2014-01-21
Yes, the AMD website says that the 270x series is supported, but you don't have a 270x series card. You have a 270 series card--they are different. I feel your pain, man, I did the same thing, I have the same exact card. I didn't realize it wasn't supported until after I ordered it, and now I'm hoping AMD releases a new driver soon to support these guys.

---

### Post by jp734 on 2014-01-21
There is actually a script to remove that. I had that issue before when i tried to use their beta driver. I'm sure you can download it somewhere.

---

### Post by Yellow Pasque on 2014-01-22
> **jp734 said:**
> There is actually a script to remove that. I had that issue before when i tried to use their beta driver. I'm sure you can download it somewhere.

...

> Beware hacks that edit binary files. If you use a hack that was made with a different version of Catalyst, you end up with a non-booting system.


---

### Post by filipe8 on 2014-11-24
> **billy.bloggz said:**
> I'm not just assuming that Catalyst would work with a recently manufactured GPU. I had heard before that AMD wasn't great with Linux support. I just took it for granted that if the AMD website said that my specific GPU was compatible with the Catalyst driver, then it is presumably currently supported hardware. Is the AMD website unreliable about information on their own drivers or is there some fine distinction between "compatible" & "supported" hardware that I am missing?

As it stands now, I decided I'd give the beta version of Catalyst a try. Now the "unsupported hardware" watermark is gone, I can actually open the Catalyst Control Center from the Application Menu and I see that it now identifies my GPU as a AMD Radeon R9 200 Series. Of course I'd prefer to run a stable version, but if that's off the table for now I guess I will stick with this.

Dear Sir.
I also have a AMD Radeon™ HD R9 270 2GB GDDR5
What best solution did you finally give to the problem?
Thanks,
Filipe

---

