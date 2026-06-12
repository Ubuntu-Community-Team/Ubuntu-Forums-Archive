---
title: "Problem with Graphics card drivers"
date: 2011-06-16
forum: Hardware
---

### Post by Sammel on 2011-06-16
I installed Ubuntu 10.04 to my new computer but I get graphics work well. I can only use resolution of 800x600. Also my monitor is unrecognised. My Graphics card is Geforce GTX 460.

I tried downloading the drivers from NVIDIA web page.
But the installation wont proceed because "X ORG drivers are in use."

I also tried following this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#How%20to%20install%20the%20NVIDIA%20driver%20in%20Ubuntu%209.10%20or%20higher]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#How%20to%20install%20the%20NVIDIA%20driver%20in%20Ubuntu%209.10%20or%20higher")
But I can't anything about NVIDIA drivers in Hardware Drivers.

What should I do to get those drivers work?

---

### Post by mastablasta on 2011-06-17
> **Sammel said:**
>  
I tried downloading the drivers from NVIDIA web page.
But the installation wont proceed because "X ORG drivers are in use."
 
 
have you tried the ones in additional drivers menu?
 
Also the message is kind of strange. ofcourse some drivers are in use. perhaps you could try booting in recovery mode (should use vesa i believe) and then performing the drivers install. 
 
i also hope you dowloaded the correct drivers.

---

### Post by Sammel on 2011-06-17
I misremembered it a bit, it's:
> ERROR: You appear to be running an X server; please exit X before installing.

And I am sure that it is the correct driver.
In Additional drivers there is no mention about Graphics Drivers.
Only thing there are drivers of my tv-card.

EDIT: Thanks, using recovery mode allowed the installation and now drivers are working.

---

