---
title: "Audio device undetected after update"
date: 2010-09-02
forum: Hardware
---

### Post by elmasry.ayman on 2010-09-02
I was working yesterday on my laptop (HP pavilion dv6736nr) every thing was hunky dory, and I installed a few updates. I open the system today and discover that the Audio driver has failed or device is undetected.

What happened?

---

### Post by Cypress421 on 2010-09-02
Try clicking the sound icon, then Sound Preferences. What do you see in the Hardware tab?

---

### Post by lidex on 2010-09-03
Did you initially update your sound drivers to get them working? If so you probably need to redo that.

---

### Post by elmasry.ayman on 2010-09-03
I see nothing in the hardware tab...

and no it worked fine without any update...

---

### Post by lidex on 2010-09-03
> **elmasry.ayman said:**
> I see nothing in the hardware tab...

and no it worked fine without any update...

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

