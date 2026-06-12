---
title: "how to force fonts config[10-autohint.conf] to act only on thunderbird"
date: 2008-09-05
forum: General Help
---

### Post by macvr on 2008-09-05
hi,
i had font problems in firefox and with my msttcore fonts, so when i was trying to correct the fonts,

i found this file: **_/etc/fonts/conf.d/10-autohint.conf_**
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<!--  Use the Autohinter --> 
  <match target="font">
    <edit name="autohint" mode="assign"><bool>[COLOR="Red"]true[/COLOR]</bool></edit>
  </match>
</fontconfig>
```
when i set it to [COLOR="Red"]false[/COLOR] all my other fonts get displayed properly

BUT i start having font problems in thunderbird, check attached pics[1-false, 2-true]
it gets even worse in the actual mails when all different fonts are in use!

i dont know how got this file in my config,*{my guess is probably came with the thunderbird install[installed via synaptics only], could some check this?}*

how do i correct his problem?
could i set this config to act only on thunderbird?

---

### Post by macvr on 2008-09-07
Bump???

---

### Post by macvr on 2008-09-08
2nd BUMP???

---

### Post by kol on 2008-09-08
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by macvr on 2008-09-30
bump?

---

### Post by macvr on 2008-10-15
bump?

---

### Post by TeXtonyx on 2008-10-15
If you want to change the size of fonts and the kind of fonts, userChrome.css does
that. You may need to google to find the different font names available, you see
that I used both Helvetica and Adobe Caslon Pro Bold   I think that Thunderbird
has a Fonts configuration menu which may provide more font-family choices.
I made this userChrome.css for a visually impaired customer. Change it as you 
like. This works for Thunderbird and Firefox, there are 2 places for userChrome.css,
so use one or the other or both. Configuring this file is the normal solution. I don't
know how your approach is applied or if it can be applied. There are a couple of
places where you can use the fonts used by the webpage, or fonts used in an email,
or you can override those choices and insist on using your own settings (a checkbox). 

"The reason I posted my userChrome.css file is that
Preferences will not make all the fonts larger that a visually
impaired person needs larger. Just change
the numbers next to mm, such as 4.5mm or 5mm or 5.5mm

Here is a copy of my userChrome.css
------------------------------------------->

window {
font-size: 5mm !important;
font-family: Adobe Caslon Pro Bold !important;
}

menubar, menubutton, menulist, menu, menuitem {
font-family: helvetica !important;
font-style: italic !important;
font-weight: bold !important;
font-size: 4.5mm !important;
}

----------------------------------------->

The xxxxxxxx will be unique letters/numbers identifying your profile.
Copy and paste the content *between* the dotted lines.
This belongs in the chrome directory and you will most likely
need to make the chrome folder with mkdir or the file browser.

/home/username/.mozilla/firefox/xxxxxxxx.default/chrome/userChrome.css

/home/username/.mozilla-thunderbird/xxxxxxxx.default/chrome/userChrome.css

To see dot files, . , you need ls -la from the command line or turn on
'Show hidden files' which is under View in the file browser. I have
fixed this problem for a hard of seeing customer which is why I
think this step is needed additionally to setting Preferences,
depending of course on the degree of visual difficulty."

---

### Post by macvr on 2008-10-15
finally a reply :) 
ok... will try altering the chrome.css as an alternative...

PS: i dont know y u thought i was visually impaired!!! i just wanted pretty letters!

---

### Post by TeXtonyx on 2008-10-15
I didn't think you were visually impaired. I created that file for a visually impaired user
which is why I said feel free to modify it (I copied and pasted from my an/other post).
I suggest that you start with just Thunderbird. See what this userChrome.css changes. 

Then go to Thunderbird, find Fonts & Encodings -> Fonts 
You can set font sizes and the font-family there, you may have to dabble.
Probably these settings can also be controlled by userChrome.css  , but
I only used userChrome.css for the preferences that couldn't be changed within TB.
font-family you find/like in TB settings can be substituted into userChrome.css (name of font)

I found Firefox trickier to work with. By default FF uses the fonts stipulated by the
webpage you visit. If you want to use all your own settings, you have to uncheck
that box which says use website settings. This can have some unpredictable
results which is why I think TB is easier to start with. You see immediate results.

---

