---
title: "Big problem with monitor or Nvidia"
date: 2008-07-28
forum: Hardware
---

### Post by ultimate_aektzis on 2008-07-28
Hi everybody.I use ubuntu hardy for about 3 months.Until friday I had used an ati radeon 9250.Due to incompatibility problems I decided to change it.SO I bought a nvidia 7600GT.The problem is that 3 days now I see my monitor "ruined".I see green lines yellow red lines etc in my monitor and as you can understand its very annoying.I installed nvidia drivers via envyNG using failsafe gnome as I couldnt do it in another way.But now I cant change my resolution.the max I can take is 800*600:(
I would be very grateful if you could help me with that.**thanks in advance**

P.S Sometimes the wired colours are appeared  during the boot process...:confused:

---

### Post by overdrank on 2008-07-28
> **ultimate_aektzis said:**
> Hi everybody.I use ubuntu hardy for about 3 months.Until friday I had used an ati radeon 9250.Due to incompatibility problems I decided to change it.SO I bought a nvidia 7600GT.The problem is that 3 days now I see my monitor "ruined".I see green lines yellow red lines etc in my monitor and as you can understand its very annoying.I installed nvidia drivers via envyNG using failsafe gnome as I couldnt do it in another way.But now I cant change my resolution.the max I can take is 800*600:(
I would be very grateful if you could help me with that.**thanks in advance**

P.S Sometimes the wired colours are appeared  during the boot process...:confused:

Ok do you have the drivers enabled and in use under system, administration, hardware drivers? If so then you may use synaptic manger and install nvidia settings and try to change your resolution with them. Use the command ```
gksu nvidia-settings
```

---

### Post by tom66 on 2008-07-28
By weird colors on bootup do you mean when it is POSTing (before it loads Ubuntu, before GRUB or the loading screen) you see the weird lines? If that's the case, it may be a faulty graphics card.

---

### Post by djxcon on 2008-07-28
Are you looking for 3D acceleration from the video card?  When you boot into 800X600, do you still get the lines on the screen.  Have you removed the ATI drivers prior to installing the Nvidia card?  Sorry for all of the questions, but this will help us understand more about the problem and isolate the issue.

---

### Post by ultimate_aektzis on 2008-07-28
@overdrank
I didnt tried this.As I said I am new to ubuntu and I didnt know it.I will try it when I come to my ubuntu pc

@tom66.Yes exactly.But it happen only one time so I cant conclude to something.It may also be the monitor becuase its a bit old and previously used.

@djxcon

Yes,I would like 3d acceleration if its possible for my card to "afford" it.When I boot on 800*600 I dont get those lines but I hadnt spent too much time on this resolution.
I didnt remove ATI drivers(basically i dont remember if I installed them as I thought that it will recognized automatically as other devices](*,).Do you think that doing the process from the beggining will solve the problem(uninstall ati,nvidia drivers,install them in via failsafe gnome...)

---

### Post by ultimate_aektzis on 2008-07-29
> Ok do you have the drivers enabled and in use under system, administration, hardware drivers?

I am not sure what do you mean but I am the only user on the pc so I am admin too.

---

### Post by ultimate_aektzis on 2008-07-29
My bad,I forgot to mention that sometimes like today morning it begins in safe mode

---

### Post by ultimate_aektzis on 2008-07-29
Is it possible to change xrog.conf resolution entry?Sorry for tto many posts but its a bit emergency to solve the problem and I am very anxious:(:confused:

---

