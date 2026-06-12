---
title: "Document formatter that works in console?"
date: 2008-10-20
forum: General Help
---

### Post by shaggy999 on 2008-10-20
I am looking to start creating some professional documents with typesetting and stuff but right now I'm stuck on a machine that can't run a gui. Is there a program in the repos that will let me get started until I have a gui-based machine (hopefully in the next month or so)?

Maybe something that uses LaTeX or some kind of markup language that I can just type in?

---

### Post by Pro-reason on 2008-10-20
Well, since you already know about LaTeX, you don't need a &#8220;document formatter&#8221;; you just need a text editor.  The main console text editors are vim, nano and emacs.  Emacs is easily installed and the other two come by default in Ubuntu.  Nano is the most user-friendly, but the others are better if you're proficient in them.

Then just type LaTeX code.  Use the &#8220;latex&#8221; or &#8220;pdflatex&#8221; command to compile a finished document.  There are commands (such as &#8220;pdftotext&#8221; from the &#8220;poppler-utils&#8221; package) that will preview the finished PDF in the console, but you will obviously lose all the advanced formatting.

---

### Post by shaggy999 on 2008-10-20
Ok, I thought I needed a special program or something. So I guess I just need to read up on latex now. :)

Actually, I have the framebuffer setup and fbi (and associated fbgs) installed so I can read pdf files on the linux framebuffer just as they are! :)

---

### Post by Pro-reason on 2008-10-20
> **shaggy999 said:**
> 

Actually, I have the framebuffer setup and fbi (and associated fbgs) installed so I can read pdf files on the linux framebuffer just as they are! :)

Ooh, how did you do that?

---

### Post by shaggy999 on 2008-10-20
It's actually pretty easy. From a clean ubuntu server setup you need to modprobe a framebuffer module (assuming /dev/fb0 is not set up by default, it wasn't for me). I went to '/lib/modules/<kernel version here>/kernel/drivers/video' and used modprobe to see what modules I had available. I chose 'vga16fb' and modprobed that. This caused the screen to blank out and come back using that driver. Then I had to edit /boot/grub/menu.lst and add "vga=0x314" to the end of the kernel boot options. There are a bunch of different options for the vga paramater but 0x314 is all that worked for me (I believe it translates to 640*480 res).

Then I 'sudo apt-get install fbi libmagick'. Libmagick is needed to translate graphics unknown to fbi like gif images.

Anyway, after that I run 'fbi imagename.jpg' and the picture pops up over the terminal! For pdfs I do 'fbgs -c -a'. fbgs is some kind of postscript converter that then calls fbi. The -c option tells it to render in color and -a tells it to autofit the page to the screen.

One caveat is that this will NOT work if you are using 'screen' and may not work if you're using ssh/remote terminal (I'm unsure of this, but I suspect it). What I do is I just log into two terminals and set the first terminal to use screen for my multi-desktop feature and then ctrl+alt+f2 to get another console and run fbi/fbgs from there. If you use elinks you can click on pictures and it will automatically call fbi to render the pictures. Or even better you can install links2 and use the -g mode to get a full gui web experience from the terminal! Although in that case I reccomend installing 'gpm' - which is a mouse poller daemon so you can use your mouse in a terminal. :)

I've been using a terminal as my primary computer for a few months now - I'm learning a lot! You have no idea how hard it was to get my wireless card going w/ ndiswrapper & WPA-PSK encryption in a terminal. :) You really get to learn to love little gems like sed, awk, and grep when you're stuck in a terminal. :)

---

### Post by shaggy999 on 2008-10-20
I forgot to mention you can also watch movies in the terminal by installing mplayer-nogui and running the command 'mplayer -vo fbdev filename'

he he...

---

### Post by pbhj on 2008-10-20
I'm curious, and I don't have a cat, what computer are you running that can't display an X session? What is the limitation, never understood the fb thingy.

---

### Post by shaggy999 on 2008-10-20
I'm running a PII 333 MHz w/ 128 MB RAM. It can run X, but X runs incredibly slow. Adding a window manager makes it run even slower.

---

### Post by NESFreak on 2008-10-21
> **shaggy999 said:**
> I'm running a PII 333 MHz w/ 128 MB RAM. It can run X, but X runs incredibly slow. Adding a window manager makes it run even slower.

how about using something like fluxbox or windowmaker as your window manager. Those run fast on even a 486.

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
[https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding%20a%20Window%20Manager](https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding%20a%20Window%20Manager)

---

