---
title: "Ati pro turbo pci"
date: 2005-04-04
forum: Hardware &amp; Laptops
---

### Post by gnomewithonesock on 2005-04-04
I am trying to run ubuntu on an old 190 mhz pc . I did the whole installation but the onboard video is not working . I get to the sign on screen and it loads gnome but theres these green lines across the screen . 

I then get some flickering of the screen and then it takes me back to the sign on screen .It does this twice and then freezes.

 So i tried another video card (ati pro turbo ) and the screen just goes blank when i am booting up . It wont even make it to the sign on screen .

I am now reinstalling with the ati card . I hope i am not wasting my time :/ (ill post back with the info , if it doesnt work or it does .

Btw , I  have also tested two seperate moniters but i am pretty sure this is a video card issue .. for me . 

Any suggestions ?  (keep in mind i am a newbie and have only used mandrake/suse  before)

---

### Post by erkki70 on 2005-04-04
Hi,
You need to post more details about your config.
What is your onboard card?
Could you post the result of the following command from terminal (or console if you don't get X to display anything):
 ```
lspci
``` 
This will list your hardware.
About the green lines for the onboard card, reconfiguring your X server might do the trick and you could try:
 ```
sudo dpkg-reconfigure xserver-xorg
``` 

Hope this helps.

Cheers,
Erkki

---

