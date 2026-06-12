---
title: "How to create and install a custom keyboard layout?"
date: 2005-11-09
forum: General Help
---

### Post by Winge on 2005-11-09
I would need some advice on how to create a custom keyboard layout. For example, I would want to create a polytonic greek layout suited for a Swedish keyboard, (and which inputs combining unicode accents, instead of using dead keys).

I don't know how to do this, but I have tried to edit the file /etc/X11/xkb/se and added a section like this:

xkb_symbols "gr" {
    include "se(basic)"
    name[Group1]="Sweden - Greek polytonic";

    key <AD02> { [	Greek_finalsmallsigma,	Greek_SIGMA	] };
// etc. etc.
};

(I don't know exactly what I'm doing here. I'm just copying the syntax from other parts of the file.)

I have also added a corresponding line in /etc/X11/xkb/rules/base.lst

However, when I try to install a different keyboard layout in Gnome, the variant I created does not show up.

Do I have to do something with xkbcomp perhaps?

Or am I completely off track? Any advice is highly appreciated.

---

### Post by Winge on 2005-12-07
I still need some help with this. :( Actually I had some success: I ended up creating a completely new file in /etc/X11/xkb/symbols/ with the name mygreek. I can then change my keyboard layout with the commands "setxkbmap mygreek" and "setxkbmap se".

However, I still have the problem that this new layout is not aknowledged by the keyboard properties dialog ("gnome-keyboard-properties") - no entry for my layout is found in the list. How do I update this list? The thing I want to achieve is to install my keyboard layout in Gnome, so that I can use the usual methods to switch keyboard layout - e.g. through the keyboard indicator menu which I can place in a panel, or with a simple press on a key.

---

### Post by precinto on 2006-12-02
This is way too late for sure. But anyways...

You can pick another language's symbol table (for example 'no' or 'pt'), one you know you won't use, back it up, and save you 'mygreek' table with the name of the other layout ('no', 'pt' or whatever you chose).

This way you can easily change layouts through the gnome menu. I know it's a little sneaky, and finding a way to create new entries in the ditribution list would be much better. But all I've found about it didn't work. So this is my best option, and works very well.

---

### Post by stepasha on 2007-07-04
It took me days, but I finally found the answer to this. I was about to post asking a similar question about how to get gnome-keyboard-properties to to show my entry, but I finally managed it.

I found the info on:
[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

Here's the short version:

You will need to add an entry that lists your keyboard variant name to: 
/etc/X11/xkb/rules/xorg.lst

Then you need to add an entry to:

/etc/X11/xkb/rules/xorg.xml

in this file you will need to add a <variant> section to the <variantList> section.

After I did that, my new Tajiki phonetic keyboard appeared in the keyboard-properties dialogue. No reboot or anything needed.

Hope this helps.

---

### Post by simosx on 2007-08-08
stepasha,
you can this keyboard layout in Linux by filing a report at
[http://bugs.freedesktop.org/](http://bugs.freedesktop.org/)
under the product "xkeyboard-config".

I am sure a lot of people will appreciate this.

---

