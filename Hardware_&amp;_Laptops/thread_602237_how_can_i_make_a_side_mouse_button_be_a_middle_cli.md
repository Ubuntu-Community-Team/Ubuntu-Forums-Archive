---
title: "how can i make a side mouse button be a middle click?"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by erlinux on 2007-11-04
i am trying to make the single side button of my [ms comfort optical mouse 3000]("http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=041") become the middle click that newtab's a link in firefox. the button is button9 and when i press the scroll wheel's middle click (button2) it copies and pastes.

the question: How can i make Button9 open new tabs for links in firefox/opera/ect.

---

### Post by bingoUV on 2007-11-04
> **erlinux said:**
> i am trying to make the single side button of my [ms comfort optical mouse 3000]("http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=041") become the middle click that newtab's a link in firefox. i have never edited text files for configuration and i am new to ubuntu, any helpful hints?

Run the command xev from a terminal. It will open a small window. Take your mouse pointer inside the window, and click the side button of your mouse. Don't move the mouse at all now. Look what is just printed on your terminal. It will be something like
```

ButtonRelease event, serial 33, synthetic NO, window 0x3c00001,
    root 0x73, subw 0x3c00002, time 13922652, (45,45), root:(50,67),
    state 0x400, **button 3**, same_screen YES

```

I have highlighted the important part. Remember what is the button number, and close the xev window. As you move the mouse to close the window, it will print lot of garbage, and your button code will be scrolled up, so remember it carefully.

The above output was for clicking the right click on my right handed mouse. This is considered button 3 by my mouse. Your side button will certainly produce a different code. Suppose it is button 4. Now do the following (the middle digit is key code of your side button)

```

xmodmap -e "pointer = 1 4 3"

```

Now see whether this is what you wanted to do. If you are satisfied, add this last command to your ~/.xsession file (if it does not exist, create the file).

---

### Post by erlinux on 2007-11-04
i updated my post

---

### Post by bingoUV on 2007-11-04
If you middle click a link, firefox pastes from clipboard? Where does it paste? There should be not pasteable region focussed when you middle click on a link. Maybe I have misunderstood something now.

---

### Post by erlinux on 2007-11-04
when i middle click on any type of highlighted text (in something you can type, like a text editor), it copies the texts and then pastes the text. i want to make the side red button work as button2. a strange thing happens in xev, when i press both right and left click on my touchpad it says button2 and this open a link in a new tab in webbrowsers, but when i middle click,


THE MIDDLE CLICK STARTED WORKING FOR OPENING NEW TABS:guitar:

but how do i make button9 do the same function as button2?

---

### Post by bingoUV on 2007-11-04
> **erlinux said:**
> when i middle click on any type of highlighted text (in something you can type, like a text editor), it copies the texts and then pastes the text. i want to make the side red button work as button2. a strange thing happens in xev, when i press both right and left click on my touchpad it says button2 and this open a link in a new tab in webbrowsers, but when i middle click,


THE MIDDLE CLICK STARTED WORKING FOR OPENING NEW TABS:guitar:

but how do i make button9 do the same function as button2?

You said you want to fix it in firefox/opera. Now you have come to text editor. It seemed from your original question that your problem is only with firefox/opera. Was it just an example?

If you want to make your side button as button 2, follow the steps I outlined earlier.

---

