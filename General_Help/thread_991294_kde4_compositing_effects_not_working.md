---
title: "kde4 compositing effects not working"
date: 2008-11-23
forum: General Help
---

### Post by bmorency on 2008-11-23
Hi,

I just upgraded from kubuntu 8.04 to kubuntu 8.10 and the compositing effects that come with kde4 do not seem to be working. I have a geforce 7800gtx video card with driver 173.14.12 installed. I have also tried the 177 version drivers but it still does not work. I have set the effects to custom and have selected a lot of different effects like taskbar thumbnails and wobbly windows but none of the seem to be working.

In a console window I type 
glxinfo | grep direct

I get:
Direct rendering: Yes

So I think my drivers are working properly. Does anyone have any ideas what the problem might be? Could it be a problem from the upgrade from kde3 to kde4 between versions? 

Thanks for any help.

---

### Post by bmorency on 2008-11-23
I have solved the problem. When I opened the Desktop Effects program I thought that was to enable the built in kwin effects. I thought I had to do that first before I went into the system settings to adjust the options I wanted. So it turns out the Desktop effects is actually compiz and it seems to conflicts with the built in kwin effects. So I removed the desktop effects and now the built in kwin effects are working.

---

