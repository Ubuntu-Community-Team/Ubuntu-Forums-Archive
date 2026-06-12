---
title: "Font Frustration"
date: 2008-09-13
forum: General Help
---

### Post by shuukazedojo on 2008-09-13
Hello everyone. I'm very excited to be part of the Ubuntu movement. I feel like the community of support has been incredible and could never be replaced by someone on a phone. THANK YOU. I would love to see everyone in the world have the opportunity to use their computers to their maximum potential without having to fork over a small treasure, goat, or savings bond. Ubuntu has been the answer. 

Moving on.

Today I had my second frustrating encounter with installing fonts. I feel like this process could be made simpler for those of us who appreciate the vision of Ubuntu but, quite frankly, just aren't up there when it comes to understanding how it all works. I know Linux isn't supposed to be super easy, but maybe that's the paradigm that needs to shift for world domination. :) After some research and help from my fiancee (who IS one of those people that is up there when it comes to understanding this stuff) I now have fonts installed. Here's how it was done:

From the desktop, press ALT+F2. This brings up the Run Application Window. In this window type "gksudo nautilus" This allows you to open Nautilus as Root so you can change things like :) fonts. 

Go to /usr/share/fonts/ and select the appropriate folder. I was installing TTF, so I went to the /truetype folder. Then click on /myfonts.

From this point you can drag and drop your .ttf files from the desktop directly to this folder. 

Next I refreshed my cache just to be sure. Open a terminal and type:

sudo fc-cache -fv


This worked for me. I don't know if it's the official way to do it or the right way, but it worked. I now have access to those fonts in Open Office, etc. which is all I wanted. Hopefully this will help someone else out there. 

UBUNTU DEVELOPERS: PLEASE, CAN WE FIND AN EASIER WAY TO DO THIS???? 

Thank you!

---

