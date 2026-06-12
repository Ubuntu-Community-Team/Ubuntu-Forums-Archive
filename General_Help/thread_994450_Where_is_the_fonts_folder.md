---
title: "Where is the fonts folder?"
date: 2008-11-26
forum: General Help
---

### Post by Meadow Marie on 2008-11-26
I have downloaded a ttf font and I want to copy it to my Fonts folder. I learned from the ubuntu documentation that the fonts folder should be in System, Preferences, Fonts. But there is not any Fonts option in the Preference menu. Please help! 

Thanks, Meadow

---

### Post by hictio on 2008-11-26
System wide fonts are on the directory '/usr/share/fonts/'.

You can install your own fonts on a hidden directory on your $HOME called '.fonts', that's DOT fonts.

To create it, open a Terminal (Applications -> Accessories -> Terminal)
And then type:

```

cd (ENTER)
mkdir .fonts (ENTER)
cd .fonts (ENTER)
nautilus ./ (ENTER)

```

Drag your font to the directory window that opened after the last typed command,

---

### Post by Meadow Marie on 2008-11-26
Hello and thank you for the advice. I did try that in Terminal but was there supposed to be anything that came up on the Terminal screen in between each line I was to type? Like if the first thing I typed was cd and then I pressed enter, was anything supposed to happen other than a brand new line showed up underneath the first as if I didn't type anything?

After typing each line, this is what my Terminal looked like:

meadow@meadow-desktop:~$ cd
meadow@meadow-desktop:~$ mkdir .fonts
meadow@meadow-desktop:~$ nautilus ./
meadow@meadow-desktop:~$

It did make a screen pop up, but was it supposed to be my Home Folder? That is what popped up.

---

### Post by hictio on 2008-11-26
You missed one.
After you create the directory, with 'mkdir .fonts', you have to change directory onto it, with:

```

cd .fonts

```

Then, issue the nautilus one, and instead of the Home directory, it will open the .fonts one.
Place that font onto the nautilus window, simply drag and drop to it.
If you want to use the new font on an already open application, you'll have to close it, and open it again to be able to use the new one.

---

### Post by Meadow Marie on 2008-11-27
Thank you so much!! It worked after I actually followed the correct directions. Haha. Have a good night.

Meadow

---

