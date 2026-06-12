---
title: "How to change the second color on title bars"
date: 2008-07-29
forum: General Help
---

### Post by guitarhero136 on 2008-07-29
I am unsure of how to change the second color of the title bar on windows. I want to make it a different color.

I attached a screenshot to help explain what I'm talking about.

Thanks in advance!

:guitar:

---

### Post by bgerlich on 2008-07-29
Probably you will have to go through the theme config files located in /usr/share/themes/YourThemeName

---

### Post by guitarhero136 on 2008-07-29
I looked through the three configuration files:

gtkrc
metacity-1/metacity-theme-1.xml
metacity-theme-2.xml

and found nothing that looked right. It was also not very easy to look at due to the fact I did not know what I was looking for.

Can anyone point me to the right section here.

---

### Post by bgerlich on 2008-07-29
Well you should have done more looking.

I'm assuming you are using the Crux theme.

In gtkrc it's the "selected_bg_color".

You are welcome.

EDIT:

Sorry my bad. For some reason I thought you meant the other bar colour. You have to edit the images in /metacity-1 dir . The names are - active-top-center-right.png - for the active bar and inactive-top-center-right.png for the inactive one. This the "center of the bar, you'll probably also have to redo the other ones for consistency.

---

### Post by guitarhero136 on 2008-07-29
alright, thanks. I will try and use that. it just seems like there would be somewhere that defines that color.

---

