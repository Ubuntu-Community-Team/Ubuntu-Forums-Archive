---
title: "change the close button location"
date: 2008-11-12
forum: General Help
---

### Post by hydraulicjj on 2008-11-12
Hi. does anyone know how i can change the location of the close button in ubuntu hardy so that it is like on osx?

---

### Post by Coreigh on 2008-11-12
I do not know where it is located on OSX, but ...

The quit button is actually a "launcher" called Quit and can be put anywhere a launcher can go.

For example to add one to the bottom panel, right-click the panel and choose "Add to Panel" and select "Quit" from the list.

Likewise if you are using AWN, add the Quit launcher to the AWN panel.

---

### Post by loomsen on 2008-11-12
I think he's talking about the window-decorator close button...

You can do this with the emerald theme manager, assuming you use emerald as your window decorator...

[[img]http://www.ubuntu-pics.de/thumb/5563/screenshot_68_XH4PIB.png[/img]](http://www.ubuntu-pics.de/bild/5563/screenshot_68_XH4PIB.png)

Which function to specify with which letter you can make up with the help below.
Starting left, the first : makes is centered, the next : right aligned.

Just take the window as an example, ```
IT::
``` is mine at the beginning, and you can see, left aligned I got the icon as well as the window title, nothing centered here, and then the other 4 functions, ANXC for set above, minimize, etc...

you may use spacers as well simply by adding the count of pixels the space should have in brackets.

I(10)T::ANXC would leave 10 pixels of space between the icon and the title.

Hope this is actually answering your question ^^

---

### Post by hydraulicjj on 2008-11-12
> **loomsen said:**
> I think he's talking about the window-decorator close button...

You can do this with the emerald theme manager, assuming you use emerald as your window decorator...

[[img]http://www.ubuntu-pics.de/thumb/5563/screenshot_68_XH4PIB.png[/img]](http://www.ubuntu-pics.de/bild/5563/screenshot_68_XH4PIB.png)

Which function to specify with which letter you can make up with the help below.
Starting left, the first : makes is centered, the next : right aligned.

Just take the window as an example, ```
IT::
``` is mine at the beginning, and you can see, left aligned I got the icon as well as the window title, nothing centered here, and then the other 4 functions, ANXC for set above, minimize, etc...

you may use spacers as well simply by adding the count of pixels the space should have in brackets.

I(10)T::ANXC would leave 10 pixels of space between the icon and the title.

Hope this is actually answering your question ^^

i wasnt using emerald but i decided to try it and it did what i wanted. thankyou

---

### Post by fugyfudy on 2008-12-26
There is a way to change it without using Emerald. 
Hit alt and F2 which will bring up the run application dialogue.  From there you type in
```
gconf-editor
```
and hit enter.  from there all you need to do is hit ctrl and f and search for metacity, click the  link that says /apps/metacity/general and then scroll down to button_layout. just click on the right side where it says menu:etc and then to get it like a mac you would have it be close,minimize,maximize:menu

---

