---
title: "How to install my Office fonts on Ibex?"
date: 2008-11-04
forum: General Help
---

### Post by darkvampire on 2008-11-04
I have a XP partition and a Ubuntu 8.10 partition.

I wanted my Office 2007 fonts for my Ubuntu, and the other few fonts which I use for my coursework.

I have copied and pasted the fonts I want to my Home folder, but how do I install them onto my system so I can use them?

This is actually quite an embarrassing question because I bet it is really simple.

Plus, I rather not install them one by one ¬¬

---

### Post by SuperSonic4 on 2008-11-04
This can/should be as user

1. ```
mkdir ~/.fonts
```

2a. (copy and paste them to the ~/.fonts folder you just created)

2b. ```
cp /media/[COLOR="Red"]320GB\media[/COLOR]/Windows/Fonts ~/.fonts
```

3.```
fc-cache
```

Only do one step 2a or 2b of course, the bit in red will be the name of your drive as it appears in Places. I'm not 100% about the space being represented by \ but 2a will work

you will then need to close and reopen your office

---

### Post by Therion on 2008-11-04
You could install the **msttcorefonts** package (search for it in Synaptic).

The Truetype Microsoft fonts provided by the package include:

    * Andale Mono
    * Arial Black
    * Arial (Bold, Italic, Bold Italic)
    * Comic Sans MS (Bold)
    * Courier New (Bold, Italic, Bold Italic)
    * Georgia (Bold, Italic, Bold Italic)
    * Impact
    * Times New Roman (Bold, Italic, Bold Italic)
    * Trebuchet (Bold, Italic, Bold Italic)
    * Verdana (Bold, Italic, Bold Italic)
    * Webdings

Does that do it for you, or do you need something else?

---

### Post by SuperSonic4 on 2008-11-04
I know Calibri features heavily in Office 2007. You can copy and paste any font using my method above.

I just copied C:\Windows\Fonts into ~/.fonts

---

### Post by darkvampire on 2008-11-04
> **Therion said:**
> Does that do it for you, or do you need something else?

I did the msttcorefonts the second I installed my Ubuntu...

I hate browsing without them :wink:

---

### Post by darkvampire on 2008-11-04
> **SuperSonic4 said:**
> I know Calibri features heavily in Office 2007.

That is that one I use for the body of all my essays ( 11pt )

(:

---

### Post by darkvampire on 2008-11-04
> **SuperSonic4 said:**
> This can/should be as user

1. ```
mkdir ~/.fonts
```

2a. (copy and paste them to the ~/.fonts folder you just created)

2b. ```
cp /media/[COLOR="Red"]320GB\media[/COLOR]/Windows/Fonts ~/.fonts
```

3.```
fc-cache
```

Only do one step 2a or 2b of course, the bit in red will be the name of your drive as it appears in Places. I'm not 100% about the space being represented by \ but 2a will work

you will then need to close and reopen your office


THANKYOU! I'll do this now :wink:  *Thanks post*

---

### Post by R2D2! on 2008-11-04
You can also have a l&#305;nk &#305;n ~/.fonts to /media/320GB\media/Windows/Fonts ; that way any font you &#305;nstall on W&#305;ndows w&#305;ll also be ava&#305;lable on Ubuntu.

&#8212;Ilhu&#305;temoc &#948;

---

