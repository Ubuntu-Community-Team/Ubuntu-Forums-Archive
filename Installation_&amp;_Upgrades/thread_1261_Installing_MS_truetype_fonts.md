---
title: "Installing MS truetype fonts"
date: 2004-10-19
forum: Installation &amp; Upgrades
---

### Post by knappen on 2004-10-19
How do I install my MS fonts in Ubuntu? And most importantly, how do I make Firefox recognise them?

---

### Post by cybrjackle on 2004-10-19
You need "universe" in your sources.list

```

sudo apt-get install msttcorefonts

```


```
$ sudo apt-cache show msttcorefonts
Package&#58; msttcorefonts
Priority&#58; optional
Section&#58; contrib/x11
Installed-Size&#58; 156
Maintainer&#58; Tollef Fog Heen &lt;tfheen@debian.org&gt;
Architecture&#58; all
Version&#58; 1.1.11
Depends&#58; wget &#40;&gt;= 1.9.1-4&#41;, cabextract &#40;&gt;= 0.1-2&#41;, xutils &#40;&gt;= 4.0.2&#41;, debconf &#40;&gt;= 1.2.0&#41;, defoma, debianutils &#40;&gt;= 1.7&#41;
Recommends&#58; x-ttcidfont-conf
Filename&#58; pool/universe/m/msttcorefonts/msttcorefonts_1.1.11_all.deb
Size&#58; 21566
MD5sum&#58; 69a1bb2e1f66f03a5b3748685d9bd973
Description&#58; Installer for Microsoft TrueType core fonts
 This package allows for easy installation of the Microsoft True Type
 Core Fonts for the Web including&#58;
 .
   Andale Mono
   Arial Black
   Arial &#40;Bold, Italic, Bold Italic&#41;
   Comic Sans MS &#40;Bold&#41;
   Courier New &#40;Bold, Italic, Bold Italic&#41;
   Georgia &#40;Bold, Italic, Bold Italic&#41;
   Impact
   Times New Roman &#40;Bold, Italic, Bold Italic&#41;
   Trebuchet &#40;Bold, Italic, Bold Italic&#41;
   Verdana &#40;Bold, Italic, Bold Italic&#41;
   Webdings
 .
 You will need an Internet connection to download these fonts if you
 don't already have them.

```

---

### Post by cybrjackle on 2004-10-19
Here is a link on how to add more, look at section 3.2

[http://www.paulandlesley.org/linux/xfree4_tt.html](http://www.paulandlesley.org/linux/xfree4_tt.html)

---

### Post by knappen on 2004-10-19
Thanks!
 
I will add universe and sudo apt-get install msttcorefonts.

After this, will Firefox recognise the new fonts? Without the ms fonts Firefox  looks pretty ordinary.

---

### Post by knappen on 2004-10-19
cybrjackle, are you the same cybrjackle on mandrakusers.org?

---

### Post by cybrjackle on 2004-10-19
[quote=knappen]cybrjackle, are you the same cybrjackle on mandrakusers.org?[/quote]

yep

---

### Post by cybrjackle on 2004-10-19
[quote=knappen]Thanks!
 
I will add universe and sudo apt-get install msttcorefonts.

After this, will Firefox recognise the new fonts? Without the ms fonts Firefox  looks pretty ordinary.[/quote]

yep

 8)

---

### Post by knappen on 2004-10-19
nice to see you here as well!

I installed the ms fonts at it works well. Hotmail still looks a bit wird though.

---

### Post by cybrjackle on 2004-10-19
[quote=knappen]nice to see you here as well!

I installed the ms fonts at it works well. Hotmail still looks a bit wird though.[/quote]

Nice to see you too, I'm everywere ;)

Some people say Debian fonts always look like crap, they look fine to me, but everyone see's things different.   :P

---

### Post by knappen on 2004-10-20
[quote=cybrjackle]Nice to see you too, I'm everywere ;)[/quote]

Ha ha, me too!

This time I think I will stay with Ubuntu for awhile. At least until the final release is out  8)

---

### Post by jeremy on 2004-10-20
It is easy to add ttf fonts, open nautilus and got to url fonts:/// - then just copy the fonts there, firefox, open office et al will see them.

---

### Post by knappen on 2004-10-20
Thats what I normally do but I was unsure if it worked with Ubuntu.

---

### Post by Vermyndax on 2004-10-21
Errr... what do you add to your sources to get universe again?  I'm coming off of Gentoo - last time I used Debian was about... two years ago?  Ubuntu seems to be doing me well though ;)

---

### Post by knappen on 2004-10-21
Open up Synaptic, it is in Computer - System Configuration.

Select Settings - Repositories

In there you can add and remove as you see fit. You will receive a warning when you add the Universe.

Do not forget to Reload after you made the changes  :wink:

---

### Post by drunken-wallaby on 2004-10-22
hi there. i have a little problem concerning the ms fonts.

i've installed them via ```
sudo apt-get install msttcorefonts
``` and it worked well. the fonts are available system-wide, in firefox,... however, i can't use them in open-office. anyone who knows how to fix this? :) thanks in advance...

---

### Post by Pulka on 2004-11-01
[QUOTE=jeremy]It is easy to add ttf fonts, open nautilus and got to url fonts:/// - then just copy the fonts there, firefox, open office et al will see them.[/QUOTE]

Everyone says this, but i can't do it because i can't seem to have privileges to do that. Before i could do that by loggin in with root user, but with ubuntu that's no longer possible. How can i install the fonts?
I already copied them to /.fonts, but they aren't available in office and other applications

---

### Post by btb on 2004-11-01
[QUOTE=Pulka]Everyone says this, but i can't do it because i can't seem to have privileges to do that. Before i could do that by loggin in with root user, but with ubuntu that's no longer possible. How can i install the fonts?
I already copied them to /.fonts, but they aren't available in office and other applications[/QUOTE]

Try to copy the fonts in **~/.fonts**. Gtk applications should now be able to find and use them. 

Futhermore, you could [check this document](http://www.openoffice.org/FAQs/fontguide.html#5) for more info about adding fonts to openoffice.

---

### Post by Pulka on 2004-11-01
ok....the fonts are now available in all programs except Open Office.
I tried that manual, but it says that in spadmin there is an option "fonts". I don't have that option.

---

### Post by Pulka on 2004-11-02
I still don't have the fonts in OpenOffice.
I managed to put the fonts in fonts:///, but still they don't appear in office.
Does anyone has an a idea of what can be done?

---

### Post by nicko on 2005-01-07
Locate your TrueType font that you want to use, cd to the directory,
and copy to /usr/share/fonts/truetype/openoffice, i.e 

"sudo cp mynicefont.ttf /usr/share/fonts/truetype/openoffice" .
The Spadmin thing seems to be lacking the Fonts tab, no doubt the next 
upgrade will have it right.    ......... nicko

---

### Post by nocturn on 2005-01-07
[QUOTE=nicko]Locate your TrueType font that you want to use, cd to the directory,
and copy to /usr/share/fonts/truetype/openoffice, i.e 

"sudo cp mynicefont.ttf /usr/share/fonts/truetype/openoffice" .
The Spadmin thing seems to be lacking the Fonts tab, no doubt the next 
upgrade will have it right.    ......... nicko[/QUOTE]

Thanks for this.
Instead of copying, you can also use ln.

```

cd /usr/share/fonts/truetype/openoffice
for i in /path-to-fonts/*.ttf; do ln -s $i; done
#Catch upper cases too
for i in /path-to-fonts/*.TTF; do ln -s $i; done

```

This will only keep one copy of the file around ;-)

---

### Post by michelbehr on 2005-05-11
> cd /usr/share/fonts/truetype/openoffice
for i in /path-to-fonts/*.ttf; do ln -s $i; done
#Catch upper cases too
for i in /path-to-fonts/*.TTF; do ln -s $i; done

I tried this but its not good because some of the font's names have special characters like spaces, so even better would be: 

```
cd /usr/share/fonts/truetype/openoffice
for i in /path-to-fonts/*.ttf; do ln -s "$i" . ; done
#Catch upper cases too
for i in /path-to-fonts/*.TTF; do ln -s "$i" . ; done
```

And the dot is to specify the directory... Thanx for the tip anyway! Just wanted to add this humble comment... ;)

---

### Post by andras on 2005-09-11
Hello,

I'm trying to install the MS fonts (sudo apt-get install msttcorefonts), but I make something wrong in updateing my source.list. I tried to update the source list from Synaptic and manually as well, but I still get this error after sudo apt-get install msttcorefonts :

Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

What shall I do? 

Thank you for your help!

Andras

---

### Post by peter07 on 2005-09-11
1) I think  msttcorefonts aren't available in ubuntu repositories. Is it true??
2) You can find msttcorefonts.deb package here:

[http://packages.debian.org/stable/x11/msttcorefonts](http://packages.debian.org/stable/x11/msttcorefonts)

---

### Post by seismicmike on 2005-10-06
```

root@lappy:~# apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

```

:confused: :confused: :confused: :confused: 
help!

---

### Post by PeaceMessenger on 2005-10-24
The fonts are there under Multiverse.

Use Synaptic Package Manager, look under the Settings Menu and choose Repositories.
Then click on Add and select the Multiverse Repositories.  It will take a little bit to load the new repositories.
msttfcorefonts will now be there. 

Mark it for Installation and choose Apply.

I just installed them myself tonight.  And after I did they were automatically in OpenOffice2.0. I didn't have to tweak anything.

---

### Post by ewschone on 2005-11-06
[QUOTE=peter07]1) I think  msttcorefonts aren't available in ubuntu repositories. Is it true??
2) You can find msttcorefonts.deb package here:

[http://packages.debian.org/stable/x11/msttcorefonts](http://packages.debian.org/stable/x11/msttcorefonts)[/QUOTE]

Thanks this worked perfectly, got a nice desktop now :D .

Only Opera doesnt seem to want to play nice, the fonts in the menu are real ugly... Oh well :confused:

---

### Post by hazza96 on 2005-11-10
I am trying to install fonts manually using the nautilus and fonts:/// method.

When I use my normal user all the fonts have a little padlock on them so I thought I would open a terminal and 'sudo nautilus'. I can now see the fonts (248 of them) but I cannot paste the new fonts in there.

I downloaded the free barcode font from here: [http://www.barcodesinc.com/free-barcode-font/](http://www.barcodesinc.com/free-barcode-font/) unzipped it so I can see the two TTF files, how do I install them?

---

### Post by brother_of_jared on 2005-12-23
Complete NooBie here..

How do I intall my .TTF I just opened on my desktop? I am using Ubuntu Breezy Badger. 

Thanks!

---

### Post by watkinsted on 2007-11-11
when i do that i get this   

ted@ted-desktop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

---

### Post by watkinsted on 2007-11-11
tyvm Peace Messenger for your answer

---

### Post by Hatticus on 2008-05-02
> **peter07 said:**
> 1) I think  msttcorefonts aren't available in ubuntu repositories. Is it true??
2) You can find msttcorefonts.deb package here:

[http://packages.debian.org/stable/x11/msttcorefonts](http://packages.debian.org/stable/x11/msttcorefonts)
I tried to get the fonts from here, but I got an error saying Error: Dependency is not satisfiable: cabextract

Where do I go from here?:confused:

---

### Post by Hatticus on 2008-05-02
Got it sorted, don't worry! :)

---

### Post by nik1979 on 2008-05-19
> **Hatticus said:**
> Got it sorted, don't worry! :)

How did you fix it? Same problem him.

---

