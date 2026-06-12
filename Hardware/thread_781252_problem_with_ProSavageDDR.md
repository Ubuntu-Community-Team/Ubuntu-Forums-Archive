---
title: "problem with ProSavageDDR"
date: 2008-05-04
forum: Hardware
---

### Post by SliderMan on 2008-05-04
Hello all. 

I got a problem with my graphic card, the card model is ProSavage8 I think. And its on board
card. The board model is MSI - P4MAM-V, and the  card chipset is P4M266A (VIA). I`m using ubuntu 8.04, and
My 3d acceleration is really slow (or none), and when I try to move folders/icons around, ubuntu just freeze. And then I have to reboot. Also when I try to play a song in the movie player, my computer just restarts (its works great on the non vid player).
Anyone can guide me how to fix that problem? 
Thanks in advance.
-Moshe.

---

### Post by SliderMan on 2008-05-04
help is really appreciate. Its really annoying using ubuntu on 800*600 resultion, without being able to play any game. :(  
thanks in advance, once again.

---

### Post by SliderMan on 2008-05-04
no one looked at my post! I really need an answer, so please, help me :(. I am so desprite. That ubuntu OS is really hard for beginners.

---

### Post by overdrank on 2008-05-04
> **SliderMan said:**
> no one looked at my post! I really need an answer, so please, help me :(. I am so desprite. That ubuntu OS is really hard for beginners.

Hi and I have never had good luck with the savage graphics myself. Have you tried to reconfigure your xorg with this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` In the past chnaging the default depth from 24 to 16 has helped but as for the 3d I can not help. This link may help in editing your xorg
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Good luck!

---

### Post by SliderMan on 2008-05-04
> **overdrank said:**
> Hi and I have never had good luck with the savage graphics myself. Have you tried to reconfigure your xorg with this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` In the past chnaging the default depth from 24 to 16 has helped but as for the 3d I can not help. This link may help in editing your xorg
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Good luck!
hey, thanks for the replay!

Yes I forgot to add those:
I found a guide in google. and that guide told me run that reconfigure script, i did, and then ubuntu just froze, and I had to restart my computer. And when I tried to reload ubuntu it just wont let me. There was a black screen with nothing on it, and ubuntu just froze again. So I had to recover the backup file again. Anyway this auto config script is a bad idea for me (anyway to reinstall the moudles of my driver?)
Another usefull info: When I tried to run X from terminal after editing the conf file, it said "no moudles found for savage".

Thanks in advance, once again.
-Moshe.

---

### Post by SliderMan on 2008-05-04
Really no one knows how to help me? should I get a new graphic card for using ubuntu? this is lame.

---

### Post by SliderMan on 2008-05-05
update: reinstalled ubuntu and now my sound card ESS 1963s dosent load too. lame.
anyway, is there anyway to load the module for my soundcard?

---

### Post by subzero316 on 2008-05-05
ESS still exists eh...try this link it ll have drivers....
[<<-----Click---->>]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-ESS_Technology")....it might not have the exact one but try a simlilar version.

---

### Post by SliderMan on 2008-05-05
thanks for the replay. ill try that
btw when i try to configure its allways gives me an error about the c compiler where can i get that? i already have gcc package tho.
there is no drivers for my graphic card? ubuntu set up FALSE one for me.

---

