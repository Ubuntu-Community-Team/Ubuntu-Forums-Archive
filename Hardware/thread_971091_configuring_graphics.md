---
title: "configuring graphics"
date: 2008-11-04
forum: Hardware
---

### Post by darkhammer8108 on 2008-11-04
im trying to get my nvidia 7900gs to work with a fresh installation of 8.10. the card keeps dropping me into a low graphics mode though to recover the xorg.conf with. i am reading a lot about this problem in other places but no one is saying how they fixed it or if they have fixed it. most of the posts relate to the release candidates and betas. i am using the release version of intrepid. 
my xorg version is 7.4
my nvidia version is 177
my kernel is the generic
rumors are that nvidia has not yet written a 7.4 compatible driver. is this true? if not how do i get the driver to work with my configuration? i have tried jockey, and nvidia-xconfig(not the package the one that is with the driver). neither generate anything usable that i can get into a session with and use nvidia-xsettings to perfect. i also tried bringing over an xorg.conf from another installation on my system and commenting out all of the lines pertaining to the fonts and stuff on that system. does anyone know what is really happening here?

---

### Post by rem on 2008-11-04
have a look on synaptic on nvidia-glx-173. as far as i understand this is the beta driver nvidia released to work with the new 8.10 and compatible with your card.

for example, i have an old video card nvidia 440 mx and for me nvidia-glx-71 works fine.

hope it helps but before installing and try using that, please ask a second opinion or google some more. sorry i cannot be more concrete about this but i just upgraded myself and still trying to figure out some things...

---

### Post by darkhammer8108 on 2008-11-04
the 173 driver gives the same results. no visible differences that i can tell.

---

### Post by rem on 2008-11-04
i am really sorry, it worked for me and this might sound like a stupid question but did you tried to adjust monitor resolution from System > Preferences > Screen Resolution after installing the nvidia-glx-173 driver ? this is how I did and I'm fine now...

---

### Post by darkhammer8108 on 2008-11-04
it crashes the nvidia driver before you get into gnome. it throws an error saying that screens were found but not usable or if the option type1 is listed it says that type1 is not found.

---

### Post by rem on 2008-11-04
i am sorry but don't have any other ideas ... i think i was lucky and it just worked for me. i had other issues though and spent the last two days on that and finally managed to sort everything out.

---

### Post by darkhammer8108 on 2008-11-04
yea unfortunately this seems like a really fundamental issue that i probably cannot resolve myself. im guessing that the nvidia driver is not compatible so i guess ill have to wait for it to show up in intrepid-updates. if anyone knows anything else though please tell me because i would really like to get ubuntu up and running fast. im looking for a lighter distro than opensuse (though i do love yast) and ubuntu has proven to work in the past besides this. if the need arises i guess i can revert to 8.04 but id like to stay as current as possible.

---

### Post by gummygod on 2008-11-18
i have a 7900gs and i had problems when i first installed 8.10 but the simple fix for me was to disconnect my 2nd monitor (my tv) from the back of my card. then magically everything works fine. not sure if you have the same problem though

---

