---
title: "Firefox Font Too Small"
date: 2008-10-07
forum: General Help
---

### Post by mike0020 on 2008-10-07
When I open Firefox the font is way too small and hard on the eyes. Is there a way for me to change the size of the font?

---

### Post by WWSmith36 on 2008-10-07
Try holding down CTRL + scrolling you wheel mouse.  This will change the size for you.

Hope this helps

---

### Post by iaculallad on 2008-10-07
> **mike0020 said:**
> When I open Firefox the font is way too small and hard on the eyes. Is there a way for me to change the size of the font?

Try tweaking Firefox's preferences: Edit->Preferences->Content->Fonts and Colors, and try changing the font size.

---

### Post by mike0020 on 2008-10-07
> **WWSmith36 said:**
> Try holding down CTRL + scrolling you wheel mouse.  This will change the size for you.

Hope this helps

I know about that but the preferences don't save when I do that, it also distorts the pictures.

> **iaculallad said:**
> Try tweaking Firefox's preferences: Edit->Preferences->Content->Fonts and Colors, and try changing the font size.

I tried that, it works but only with some fonts. Like it changed the font on Google, but the font on these forums (and many other sites) stays the same.

---

### Post by iaculallad on 2008-10-07
You could try installing the M$ corefonts:

```
sudo apt-get install msttcorefonts
```

---

### Post by kaibob on 2008-10-07
Did you remove the check from the Firefox preference: "allow pages to choose their own fonts, instead of my selections above"?

---

### Post by TeXtonyx on 2008-10-07
I use userChrome.css (google it) for both Firebox and Thunderbird and it can make the
fonts of File Edit View History larger and darker and also the dropdown menus. 
Here is a copy of my userChrome.css
----------------------------------------------------------

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

-------------------------------------------------------
Then as they said you can do some stuff with Tools->Options->Content->Advanced
and I also turn off using the website I'm visiting default font settings. The file goes to
C:\Documents and Settings\Owner\Application Data\Thunderbird\Profiles\gzcuwgqq.default\chrome
C:\Documents and Settings\Owner\Application Data\Mozilla\Firefox\Profiles\1y7unns9.default\chrome
Those are the Windows locations, put it the correct place for the Ubuntu installation.
I also use NoSquint, [http://urandom.ca/nosquint/](http://urandom.ca/nosquint/)  and magnifying web pages to 120% It is a standard FF plugin.

---

### Post by Therion on 2008-10-07
Go to...

Edit/Preferences/Content tab.

Fonts & Colors section - Advanced button.

Set the "Minimum Font Size" drop down menu to 14 maybe 16...  Something along those lines should do it, but use whatever setting works for you.


Edit:  You can also over-ride page specified fonts and "force" fonts of your own choosing by un-ticking that little box that says "Allow pages to use their own fonts..." in that same dialog box.

---

### Post by TeXtonyx on 2008-10-08
The reason I posted my userChrome.css file is that 
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

The xxxxxxxx will be unique letters/numbers identifying your computer.
Copy and paste the content *between* the dotted lines.
This belongs in the chrome directory which you will 
need to make with mkdir or the file browser.

/home/username/.mozilla/firefox/xxxxxxxx.default/chrome/userChrome.css  

/home/username/.mozilla-thunderbird/xxxxxxxx.default/chrome/userChrome.css

To see dot files, . , you need ls -la from the command line or turn on 
'Show hidden files' which is under View in the file browser. I have 
fixed this problem for a hard of seeing customer which is why I 
think this step is needed additionally to setting Preferences, 
depending of course on the degree of visual difficulty.

---

