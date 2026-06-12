---
title: "Change Bash Colours"
date: 2008-09-18
forum: General Help
---

### Post by thelucster on 2008-09-18
Hi all,

I have recently changed my terminal to use a transparent-black background. Unfortunately this results in some of the colours being unreadable, can anyone give me a link to a page where I can change the colours used by Bash? I know it exists, I just can't find it!

Regards,

Luca Spiller

Nb: I don't want to change my prompt, I want to change the actual shade of the colours.

---

### Post by mcduck on 2008-09-18
Why not change them directly from your terminal's settings? At least if you are using the Gnome-terminal you can configure the colors from the gnome-terminals profile settings..

---

### Post by mb_webguy on 2008-09-18
If you're using gnome-terminal, you can change the colors used in the same section of the preferences where you changed the background.  On the Colors tab, the top section lets you specify foreground and background colors, and the bottom section lets you specify the color palette.

However, if you're intent on changing the colors of the bash shell itself, you should find [this link]("http://www.systhread.net/texts/200703bashish.php") helpful.

---

### Post by thelucster on 2008-09-19
Hmm, I thought there was a standard way to switch the colour pallete, no matter what terminal is used. Oh well my mistake!

I regularly SSH into a couple of Ubuntu servers from different machines (and on different platforms), so a standard way would be easiest, but it appears it doesn't exist!

Cheers for your help anyway!

---

### Post by SBFC on 2008-09-19
You can adjust the colors for all shells (aterm, rxvt, xterm, etc) but you'd have to apply this method to the hosts you ssh into as well for the effect to carry.

In your .bashrc file is the following line:

```
eval "`dircolors -b`"
```

To get more info on the following view the man page for 'dircolors'. Anyway, create a file using the output of 'dircolors --print-database'

```
dircolors --print-database > .dircolors
```

Then change .bashrc to look like this:

```
eval "`dircolors -b .dircolors`"
```

Now you can open up .dircolors and adjust the color settings for all file types. There are comments explaining what the codes are for the attributes, text colors, and directory colors.

---

