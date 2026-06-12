---
title: "Firefox Isn't Rendering Webpages Properly"
date: 2008-07-24
forum: General Help
---

### Post by Yorkshireman on 2008-07-24
Recently I reformatted my computer and due to the incompetence of the disk management utility of my Windows Setup Disc my hard drive partitions aren't what I'd like them to be. The utility told me I had about 124000MB's to play with and so I did: 120,000MB (roughly 120GB) for my system partition and then another 4000MB (roughly 4GB) partition for my network drive. I then come to look at the Disk Management utility in Computer Management and it turns out I have some 20GB's of unpartitioned space.

So, what to do with this space?
I decided on installing Ubuntu because I have used it before, for a little while, and liked it so I wanted to try it out (see if I could replace Windows with it {since Windows has been a huge pain in my *** as of late}). So yeah, I installed Ubuntu with no flaws--surprisingly--and played around a little after doing numerous updates from the 7.10 edition I had on disc from Ubuntu. It came to exploring the Internet with Ubuntu and I was thinking this wouldn't be a problem; I use Firefox all the time in Windows; if anything, this is where I was expecting no problems... as sods law would have it, it was the first place where I came across problems; starting with Flash, Shockwave and some other plug-ins for Firefox, anyhoo, eventually I got these sorted--successfully installed.

So where's the problem you now ask?
Well, it most probably won't be a problem for the majority, if not all, of you. However, me being the perfectionist little wazzock I am I like things either better than what I am used to, or, exactly as to what I am used to; this brings me onto how either Firefox 3 or Ubuntu renders webpages. Firefox 3 in Windows everything renders fine, however, in Ubuntu things are different--I am guessing because of the drivers available to Ubuntu for my graphics card aren't all that good(?)--either way it's not a nice view; as the screenshot below demonstrates, it doesn't look nice and makes it difficult to read the text, for a starters.

[[**Using Ubuntu Firefox 3**](http://jason.thesmokylounge.com/images/not_good.PNG)]
[[**Using Windows Firefox 3**](http://jason.thesmokylounge.com/images/this-is-how-i-like-it.PNG)]

So, from looking at the two screenshots you can see Ubuntu is looking, well, ...crap? In the screenshot Ubuntu doesn't look too bad because you can zoom in, but in practicality/reality it really is awful.
I had thought of editing the fonts/colouring in the Edit --> Preferences menu to make the font and colours of the text the same but no luck there. I also tried a different browser; this browser being Opera. Now Opera started with problems: I find it mind boggling to install Flash, Shockwave and other plug-ins for this damn browser in Ubuntu so I gave up on that, anyway back to the problem in hand: the index page for IPS forums does look better; it's clearer and more crisp (so now I believe it isn't to do with the graphics card), so now, I am confused on what to do.

**_What to do?_**[list=1]
   [*]Do I find a means of installing Flash /etc in Opera and annoyingly settle for it (REALLY don't want to do this, in fact, if I have to settle for this I'll most probably ditch Ubuntu).
   [*]Is there a way to fix my Firefox 3 problem?
   [*]Any other suggestions?[/list]

[COLOR="Silver"]*The above is copied/pasted from a previous posted topic, so some parts may be irrelevant.*[/COLOR]

---

### Post by Orlsend on 2008-07-24
In Some boards if you are not loged in, then the images wont be shown or the quality degreaded...I really dont think its FF... Maybe fonts makes it look crappier?

---

### Post by cpetercarter on 2008-07-24
Have you installed the Microsoft true type core fonts? See [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/]("http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/")

---

### Post by Yorkshireman on 2008-07-24
> **Orlsend said:**
> In Some boards if you are not loged in, then the images wont be shown or the quality degreaded...I really dont think its FF... Maybe fonts makes it look crappier?
No, that isn't how this particular board works.
Anyway, another user is suffering from the same problem--the feedback we're getting is to do with fonts and such.

> **cpetercarter said:**
> Have you installed the Microsoft true type core fonts? See [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/]("http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/")
Thank You, I will try this out.

---

### Post by Yorkshireman on 2008-07-24
> **cpetercarter said:**
> Have you installed the Microsoft true type core fonts? See [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/]("http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/")
It appears that, that link/article is a little dated; for one, Software Properties is no where to be found (I am using Ubuntu 8.04)

Anyway, I did get the fonts installed thanks to outsourced help.

My latest problem is now that it is a little better, but the text/character edges aren't all that crystal clear; does anyone have any suggestions?
I have played about with System -> Preferences -> Appearance and in here, the Font tab and it has improved things but I am wondering is there any further tricks?

Also, before I upgraded to Ubuntu 8.04 I played with Display & Graphics settings or something, basically, it let me select my monitor's manufacturer and model along with my graphics card manufacturer and model. It didn't have my monitor's manufacturer (and thus didn't have my model) so I just set it to 1280 x 1024 (LCD) and then the hertz to the max which was 60Hertz. From there I selected nVidia as my graphics card manufacturer and my model wasn't there so I selected the Geforce 6 Series (because mine is Geforce 6200) after doing this my Hertz option changed to something lower than 60Hertz, so then I went back in the settings and changed the model to Geforce and then my hertz changed again, so now I went back to the monitor settings and went back to the general Plug 'n' Play option which then put my hertz to 55 or something--got confusing ...so I decided to upgrade to 8.04 (from 7.10) and hope for the best.
Now I am left with: 1280 x 1024 as my resolution and 50Hertz as my refresh rate, and I am unable to go back to that setting window because it is no longer an option (as I am sure you know).
In Windows my graphics card is easily capable of 75Hertz at the same resolution and during the Live CD period I was able to select 75Hertz, why is that I can't anymore? I figure it's to do with drivers available to Ubuntu for my graphics card? :confused: Further more, could any of this have anything to do with my problem with rendering text/characters (though, to be fair, the remainder of Ubuntu and most pages are fine).

---

### Post by geecee on 2008-07-25
G'day Mate. I think we might have the same problem. What do you think?

I am running FF 3.0.1 on my Kubuntu laptop. I have noticed that on some web pages, FF3 does not reproduce images clearly. There are no such problems when using Konqueror. 

At this URL you will find screen shots of a page displayed in FF3 and the same page displayed in Konqueror. The original image is also there.
[http://tempy.ubeauty.fastmail.com.au/](http://tempy.ubeauty.fastmail.com.au/)

The page is also OK using FF2 on my Vista box.

Have tried installing TT Fonts but made no difference.

---

### Post by Yorkshireman on 2008-07-25
Your problem appears to be with images, not characters/text. May I suggest that you play about with the **Screen Resolution** settings; try the hertz.

I'm having difficulties trying to work out what hertz amount works for me in Ubuntu. 75Hertz is lovely in Windows but that isn't an option in Ubuntu, besides which, any of the hertz only appear to make a small difference; things still seem blurry.

[COLOR="Gray"]**Edit:** OK, so I feel that this is the best it is going to get (this issue) and I feel like I am getting used to it, so I am happy for a moderator to mark this topic as Solved.[/COLOR]

---

### Post by konungursvia on 2008-08-13
Just try choosing "zoom text only" in View. It will make FF3 like FF2.

---

### Post by Master Chief on 2008-08-13
> **Yorkshireman said:**
> ...

[[**Using Ubuntu Firefox 3**](http://jason.thesmokylounge.com/images/not_good.PNG)]
[[**Using Windows Firefox 3**](http://jason.thesmokylounge.com/images/this-is-how-i-like-it.PNG)]

So, from looking at the two screenshots you can see Ubuntu is looking, well, ...crap? In the screenshot Ubuntu doesn't look too bad because you can zoom in, but in practicality/reality it really is awful...

For the record: I checked the CSS of this forum and the color produced by Mozilla (Firefox) for example for rgb(102, 102, 102) is spot on, as in exactly what is should be. Its just the fonts being different, and you had to get used to it (don't try OSX or you will cry fool every single minute).

---

### Post by TANGO! on 2008-09-11
I came through this post 'cause I was having a different problem; the images in firefox weren't looking good in my ubuntu.  Because of the post by konungursvia I reset the zoom and now the images look fine.  Just thought I'd share that info.

It's in View>Zoom>reset

About the question at the beginning of this topic, I think this is just one of those many differences in the way the different browsers render CSS.  You might want to contact the webmaster of that forum and let him know about this problem, and suggest that they test the page in different browsers.  Also, you could download the web developer toolbar for firefox and look for the CSS command that's causing the problem with the Edit CSS section.

---

