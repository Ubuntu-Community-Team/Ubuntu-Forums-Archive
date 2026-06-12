---
title: "[SOLVED] Typing in Polish on an English system (how?)"
date: 2008-09-22
forum: General Help
---

### Post by pwaugh on 2008-09-22
Someone already recommended I try System > Admin > Language Support, but that did not seem to help me at all.

Can someone walk me through how I can setup Ubuntu to allow me to type on my English (US) system with a US keyboard in Polish?  In other words, how I can type the special characters I will need to write some polish words?

I want to be able to save documents with english and polish writting.

Thanks, patrick

---

### Post by prshah on 2008-09-22
> **pwaugh said:**
> Someone already recommended I try System > Admin > Language Support,

First, install polish language support through the above.

Next, Open System-Preferences-Keyboard-Layouts-Add-Poland-OK.

Next, Press Alt+F2, and give the command```
setxkbmap
```

Next, to the Upper (or lower, as per your preference) panel, right-click and "Add" the "Keyboard Indicator" applet. 

Click on this applet to switch between English and Polish layouts.

You will need to add "setxkbmap" to your startup sessions with System-Preferences-Sessions-Startup Programs-Add-Command```
setxkbmap
``` for this setup to be remembered across reboots / restarts.

---

### Post by pwaugh on 2008-09-22
Ok, I did the above, but I still am not sure how to actually get a polish character to appear once I click on the USA in the keyboard indicator and get it to say POL.

Let's say I open gedit... how do I get say a Polish Z to appear?

Patrick

---

### Post by Icebear on 2008-09-22
To install additional keyboards goto
system>preferences>keyboard

Then hit the layout tab and hit add button

I believe you have already done this

for changing the keyboard when in the layout tab hit the layout option button

then choose the layout switching and choose what key you want to use

if you want a keyboard indicator on the panel go to a empty space on the panel and click the right mouse button and choose "add to pannel"

then scroll down to keyboard incdicator

---

### Post by pwaugh on 2008-09-22
> **Icebear said:**
> To install additional keyboards goto
system>preferences>keyboard

Then hit the layout tab and hit add button

I believe you have already done this

for changing the keyboard when in the layout tab hit the layout option button

then choose the layout switching and choose what key you want to use

if you want a keyboard indicator on the panel go to a empty space on the panel and click the right mouse button and choose "add to pannel"

then scroll down to keyboard incdicator

I can do all this, but I still do not understand how I can then type a foreign character.

---

### Post by prshah on 2008-09-22
> **pwaugh said:**
> I can do all this, but I still do not understand how I can then type a foreign character.

Open System-Preferences-Keyboard-Layouts; Click on Polish and then click the Print button to get a mapping (layout) of polish characters to the US keyboard.

Find your "Z" on this layout, and press the corresponding key on the keyboard. Ensure your keyboard indicator shows "POL".

If it doesn't work, check to make sure that you've launched "setxkbmap" and/or added it to your startup sessions as highlighted in my last post.

---

### Post by pwaugh on 2008-09-23
> **prshah said:**
> Open System-Preferences-Keyboard-Layouts; Click on Polish and then click the Print button to get a mapping (layout) of polish characters to the US keyboard.

Find your "Z" on this layout, and press the corresponding key on the keyboard. Ensure your keyboard indicator shows "POL".

If it doesn't work, check to make sure that you've launched "setxkbmap" and/or added it to your startup sessions as highlighted in my last post.

Ok, again, all this is setup.  But, how do I use it????

I open gedit, and click the indicator on the panel to change to POL, and the special polish Z is mapped to the Z key.  In fact, there are four characters mapped to this key upper & lower case Zz, and the Z's with dot's on top (polish z's).  But when I press Z, I only get english Z's.

How do I get a polish Z?????

I am running setxkbmap, and confirm it's running with:

ps -aux | grep setxkbmap

Patrick

---

### Post by prshah on 2008-09-23
> **pwaugh said:**
> Ok, again, all this is setup.  But, how do I use it????

I open gedit, and click the indicator on the panel to change to POL, and the special polish Z is mapped to the Z key.  In fact, there are four characters mapped to this key upper & lower case Zz, and the Z's with dot's on top (polish z's).  But when I press Z, I only get english Z's.


I'm handicapped by not knowing any polish, but are there any polish alphabets in this?
```
[SIZE="5"]&#261; &#8221; &#263; ð &#281;  &#273; &#331; &#295; &#8594; &#312;  &#322; µ &#324; ó  þ @ ¶ &#347; &#359;  &#8595; &#8220; &#322; &#378;  &#8592; &#380;[/SIZE]
```

If you have 4 alphabets mapped to a key, you need to enable a "3rd level chooser"; right click the "Keyboard Indicator" applet, choose "Keyboard Preferences"->Layouts->Poland->Layout Options->Third level choosers, and select whichever method you feel is most convenient to you. Now go back to gedit and try again.

---

### Post by pwaugh on 2008-09-23
> **prshah said:**
> I'm handicapped by not knowing any polish, but are there any polish alphabets in this?
```
[SIZE="5"]&#261; ” &#263; ð &#281;  &#273; &#331; &#295; &#8594; &#312;  &#322; µ &#324; ó  þ @ ¶ &#347; &#359;  &#8595; “ &#322; &#378;  &#8592; &#380;[/SIZE]
```

If you have 4 alphabets mapped to a key, you need to enable a "3rd level chooser"; right click the "Keyboard Indicator" applet, choose "Keyboard Preferences"->Layouts->Poland->Layout Options->Third level choosers, and select whichever method you feel is most convenient to you. Now go back to gedit and try again.

Hi, the last Z (with the dot) is a polish character as well as the character just to the left of it.  There is only two alphabets mapped to a key, but with upper and lower case.

Again, I open gedit, and have POL selected on the panel, and I can only type z and Z, in other words, how do I get the other z?

Telling me to do what I have already done is not going to help.  Is there some other key I need to press or something to get the alternate polish character?

Patrick

---

### Post by pwaugh on 2008-09-23
Ok, I finally got it.  I can now type my &#379;.

---

