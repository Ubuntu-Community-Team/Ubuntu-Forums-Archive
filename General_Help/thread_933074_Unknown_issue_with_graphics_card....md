---
title: "Unknown issue with graphics card..."
date: 2008-09-29
forum: General Help
---

### Post by xeriouxi on 2008-09-29
Hi!

I seem to be having an issue in getting Ubuntu running on my brother's PC. It's not a state of the art PC or anything but it works fine for what he needs.

The trouble began when I tried to update the graphics card drivers under Vista for him. When the PC rebooted it seemed to boot up fine until after the loading bar... then it just got stuck on a black screen and wouldn't move. I up/downgraded (hehe!) him to XP  and the same thing happened when I upgraded the drivers, too.

I tried Ubuntu and it worked fine until I activated his desktop visual effects. It asked for a reboot, showed the Ubuntu logo and loading bar and then just sat at a black screen and wouldn't move. Obviously it's the nVidia drivers that are the culprit here, but I didn't think that the Linux drivers would do this, too. He has a GeForce 8400 GS card. Can anyone think of why this might be happening? There's no signs of any problems in actually using the card but that's using the really old drivers he got with his machine.

Thanks for any help you might be able to give me! Sorry if I posted this in the wrong place, BTW! I'm just unsure of if it's a hardware issue or not. =)

---

### Post by tariquepark on 2008-09-29
hi there
it sounds suspicious to me
maybe hardware related, is it nice and clean inside the case?
an overheating card can do really strange things
give it a good clean inside as i said and make sure the cpu fan and heatsink are nice and clean too
the fact that you have issues in windows as well makes me think its not a driver thing.
i was wrong once before though !! :)

---

### Post by xeriouxi on 2008-09-29
> **tariquepark said:**
> hi there
it sounds suspicious to me
maybe hardware related, is it nice and clean inside the case?
an overheating card can do really strange things
give it a good clean inside as i said and make sure the cpu fan and heatsink are nice and clean too
the fact that you have issues in windows as well makes me think its not a driver thing.
i was wrong once before though !! :)

The case and card etc. is all clean and fine, yeah. As said it works flawlessly with no issues using the provided drivers but obviously I can't use them with Ubuntu. Obviously the drivers aren't liking the 8400 GS much for some reason. =(

One of the bigger problems that he's going to suffer from here is that a lot of the newer games require the later driver releases and that's not possible for him. Most of them will work fine under Wine though for him which is why I'm pinning my hopes on Ubuntu being able to work somehow with his machine...

---

### Post by tariquepark on 2008-09-29
while its not something i would suggest as a fix but you could see if there is a video bios update for the card from the manufacturers website. if the card is not that new it may have a bug which would be listed in the docs for that particular bios. however if there is no mention of this type of issue then i would be hesitant to do it
its a last resort :)
other than that im at a loss to explain it
still bugs me but lol
maybe if you have an old vid card you could try or even better another identical card to swap with to maybe eliminate or prove it as a harware problem or not
in the meantime i will keep thinking!!

---

### Post by Idaho Dan on 2008-09-29
I could not get my 8600GT to work right until I installed Envyng from the synaptic package manager. I hope this helps for you.

---

### Post by xeriouxi on 2008-10-03
> **Idaho Dan said:**
> I could not get my 8600GT to work right until I installed Envyng from the synaptic package manager. I hope this helps for you.

I tried this and it still didn't work. Funny enough I had to start a new thread a few days ago because the GeForce FX 5200 is doing **exactly** the same thing on another PC! I can't for the life of me figure out what caused this... Windows XP that was being used on the PC just suddenly stopped booting... I tried Ubuntu and it game the exact same issues as the 8400 GS mentioned in this thread. Both run AGP so I'm sure that's a culprit but nobody seems to know what to do.

Someone suggested something along the lines of "NvAGP" "2" or something in the X config file, but I don't know where it would go or when I would put it in or anything. 2 out of 3 PC's in the house now are not working right because of the stupid nVidia drivers! =(

---

