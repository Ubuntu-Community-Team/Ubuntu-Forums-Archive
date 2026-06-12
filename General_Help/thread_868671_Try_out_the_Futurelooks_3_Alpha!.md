---
title: "Try out the Futurelooks 3 Alpha!"
date: 2008-07-24
forum: General Help
---

### Post by Mazza558 on 2008-07-24
I've been working on this ever since the release of Futurelooks 2 (see signature), but want to see what people think before going any further with it.

Please bear in mind that this is in no way finished, and still has several known issues with it. Don't let that put you off trying it though - it still works as well as other themes. 

You can help (and speed up) the development of this theme by:

- Simply trying it out and posting feedback here
- Trying it out and finding bugs (other than the ones mentioned below)
- For the more skilled themers, fixing the known issues/bugs mentioned below.

I'll be able to respond for the rest of today, but will be away for the following week. Please keep offering feedback during that time - I'll be sure to take a look later.

To install:

- Download "futureosis.tar.gz" to your desktop
- Open "Appearance" 
- Drag the file from wherever you saved it into the appearance window
- Apply the theme from the appearance window

Known issues:

- Firefox does not correctly follow the spacing of menu items. The "file/edit...etc" menu has too much space between the buttons.
- When an application wants attention, the button in the task list will fade in and out of black. This needs to be a different, more visible colour.
- There is a background bar for horizontal scrollbars but not vertical. This is intentional - which looks better to you?
- Some colours don't match
- Horizontal arrows are different to vertical. 
- Scrollbars are too bright and too big. This can be fixed easily but I'll do that at a later stage.
- When opening new applications, the new task list button flashes black once before the pixmap appears.

---

### Post by Mazza558 on 2008-07-24
Any thoughts?

---

### Post by theolster on 2008-07-24
I love this.

I do dislike the size & colours of the scroll bars.  I look forward to seeing future revisions.

---

### Post by Darkshade on 2008-07-24
I'm gonna try it and comment as soon as I get on my PC, but I have to say that it looks promising

---

### Post by esac on 2008-07-24
> **Mazza558 said:**
> Any thoughts?

I can't seem to get it installed. I'm running compiz/beryl, with the standard gnome window decorator. I dragged the .tar.gz file like you said, and it reports that it was correctly installed, however nothing new shows up in the Theme list.

The inactive window titlebar is transparent.. is this it? If so how do I get the taskbar to look like yours?

---

### Post by COLiNx86 on 2008-07-24
Looks nice, but it's not my style.

---

### Post by zerocoolmax on 2008-07-24
> **esac said:**
> I can't seem to get it installed. I'm running compiz/beryl, with the standard gnome window decorator. I dragged the .tar.gz file like you said, and it reports that it was correctly installed, however nothing new shows up in the Theme list.

The inactive window titlebar is transparent.. is this it? If so how do I get the taskbar to look like yours?

same problem...

---

### Post by Mazza558 on 2008-07-24
> **esac said:**
> I can't seem to get it installed. I'm running compiz/beryl, with the standard gnome window decorator. I dragged the .tar.gz file like you said, and it reports that it was correctly installed, however nothing new shows up in the Theme list.

The inactive window titlebar is transparent.. is this it? If so how do I get the taskbar to look like yours?

Can you check in your home directory, in the ".themes" folder, that the "FutureOsis" theme folder's there? 

is there a gtkrc file in that folder?

---

### Post by esac on 2008-07-24
> **Mazza558 said:**
> Can you check in your home directory, in the ".themes" folder, that the "FutureOsis" theme folder's there? 

is there a gtkrc file in that folder?


This is what I have:


```

rayben@rayben:~/.themes$ ls
FutureOsis
rayben@rayben:~/.themes$ cd FutureOsis/
rayben@rayben:~/.themes/FutureOsis$ ls
gtk-2.0  index.theme
rayben@rayben:~/.themes/FutureOsis$ cd gtk-2.0/
rayben@rayben:~/.themes/FutureOsis/gtk-2.0$ ls
Arrow   Menu           Panel         Scrollbar        Tooltip
Button  Menubar        Progress Bar  Scrolled Window  Tree View
Entry   Miscellaneous  README        Shadow           userChrome.css
gtkrc   Notebook       Scale         Toolbar
rayben@rayben:~/.themes/FutureOsis/gtk-2.0$ 


```

---

### Post by zerocoolmax on 2008-07-25
```
 jeff@ubuntu:~/.themes$ ls
aud-Default  FutureOsis
jeff@ubuntu:~/.themes$  cd FutureOsis/
jeff@ubuntu:~/.themes/FutureOsis$ ls
gtk-2.0  index.theme
jeff@ubuntu:~/.themes/FutureOsis$ cd gtk-2.0/
jeff@ubuntu:~/.themes/FutureOsis/gtk-2.0$ ls
Arrow   Menu           Panel         Scrollbar        Tooltip
Button  Menubar        Progress Bar  Scrolled Window  Tree View
Entry   Miscellaneous  README        Shadow           userChrome.css
[COLOR="Red"]gtkrc[/COLOR]   Notebook       Scale         Toolbar
jeff@ubuntu:~/.themes/FutureOsis/gtk-2.0$ 
 
```

---

### Post by mech7 on 2008-07-25
Scroll bars dont look so nice i think... rest looks good :

---

### Post by Boktai1000 on 2008-07-27
Good work, I've been following since Futurelooks2.0 and I've been awaiting 3.0 since, can't wait till it hits final :)

---

### Post by innocenceisdeath on 2008-07-29
Thanks for this! Looking great, but I have to agree, the scroll bars aren't looking so good.

---

### Post by PRGUY85 on 2008-07-30
Scroll bars look a bit plain and Mac-ish.  Yet I like the overall feel of it.  I read somewhere (maybe Digg) that you are part of the Ubuntu theme team so I hope to see something along these lines (maybe with orange instead of blue to fit the ubuntu theme) in the Intrepid Ibex release.

You still using Crashbit and the old Futurelooks 2 Emerald themes with this?

---

### Post by SlalomMan on 2008-08-03
To all that are having problems with the theme; it looks like FutureOsis is a control theme; so what you have to do is select your theme, hit "customize" and under the controls tab you should see FutureOsis.

Hope that helps.

Also: I found that gnome-do's color is related to the "selected" color; since the alpha theme doesn't support changing of colors, I'm stuck with a black gnome-do on my blue background. I know it's an alpha, but just wanted to make sure you would remember to put this in.

---

### Post by Sain on 2008-09-07
Hey, what's the status of Futurelooks 3 development? I've been following this since the start, I really like this theme and would like to see final version... :)

Cheers,
Ivan

---

### Post by Mazza558 on 2008-09-07
> **Sain said:**
> Hey, what's the status of Futurelooks 3 development? I've been following this since the start, I really like this theme and would like to see final version... :)

Cheers,
Ivan

If anyone wants to carry on with this theme, they can do. However, I've moved back to a faster and more stable theme for now. Pixmap themes are just too slow for everyday use. 

I'm currently working on the various emerald themes and icons, having pretty much completed the gtk.

---

### Post by Sain on 2008-09-07
That's too bad, this theme really looked nice :(

Off topic: There are fast and slow themes? Didn't know that :-/

---

### Post by Mazza558 on 2008-09-08
> **Sain said:**
> That's too bad, this theme really looked nice :(

Off topic: There are fast and slow themes? Didn't know that :-/

Yeah, Pixmap themes are slower due to their size (each button is an image, for example)

---

### Post by Sain on 2008-09-08
How do I know if a theme is pixmap or not? (sorry, I'm a little green here :))

---

### Post by Mazza558 on 2008-09-08
> **Sain said:**
> How do I know if a theme is pixmap or not? (sorry, I'm a little green here :))

You have to look into the .themes folder in your home directory (it's a hidden folder). Find the theme you're looking for, and if there's just a file called "gtkrc", then it's not a pixmap theme. If it has lots of folders with all the buttons and scrollbars etc, it's probably a pixmap theme.

---

### Post by houdodu on 2008-12-08
you really should complete this theme. it was the best thing going and many people have the horsepower for "slower" themes these days.

---

### Post by Mazza558 on 2009-01-21
It's indeed fast enough, but one problem still remains: The very annoying black flash before a program loads. Other than that, I have actually been (very slowly) tweaking and improving the theme to be usable. I don't really want to go any further unless that's fixed.

On the other hand, I've been playing around with the new Murrine engine, and might do some more theme-building. Could FL3 actually be released? :o

---

