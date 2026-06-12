---
title: "Bizarre problem on my desktop"
date: 2008-08-02
forum: General Help
---

### Post by Todaro on 2008-08-02
Dear folks,

I'm a novice on Linux and this is my first post on this forum. I googled a lot before deciding to post here, I couldn't find help anywhere, so please be patient with me.

I've got Ubuntu 8.04 (hardy) running on a Core 2 Duo 2.2 GHz CPU with NVidia GeForce 8400 graphic card and a 19" widescreen with standart resolution of 1440 x 900.

Everything was going OK until I decided to choose a lower screen resolution for testing a website I develop. I set it to 1024 x 768 for a while but, when I turned it back to 1440 x 900, part of the desktop moved to the left and went out of the screen. This is what I mean:

[IMG]http://br.geocities.com/marcelotodaro/tela.jpg[/IMG]

Now it happens only on 1440 x 900, not on any other.

How could I solve this please? :confused:

Thanks!

---

### Post by dentaku65 on 2008-08-02
Set the desired screen resolution and reboot your box; then, in the Grub menu choose recovery mode, the machine starts in console mode and at the end show up a menu: choose xfix, then reboot again in normal way. The screen resolution should be fixed.

---

### Post by coffeecat on 2008-08-02
Before you try that, try something simpler. I don't know whether it will work, but it's worth a go.

Simply restart the xserver by pressing ctrl-alt-backspace. Close down any running apps first. You'll be dumped back to the log in screen. Log in again.

---

### Post by Todaro on 2008-08-02
Thanks cofeecat and dentaku65.

cofeecat, unfortunately the procedure you suggested didn't make any effect.

But dentaku65's tip was precious and solved the problem. Thank you so much!

---

### Post by BuntuFreak on 2008-08-02
I have almost the same exact problem. The difference is only that my screen is shifted to the right instead of the left.

I tried what you said with XFIX. But it did not solve my problem. Any other ideas?

---

### Post by scearley on 2008-08-03
I had similar problems.  No screen resolutions over 1280x960 would size right on my monitor.  They would either hang left, exactly like yours, or more confounding, would "creep" as many as 60 pixels of additional real estate below the bottom of the screen, making larger dialogs unusable since I couldn't get to the buttons at the bottom.

What made my problem worse was that the Screen Resolution was suddenly no longer accesible from any of my menus.

In the end, I ran [FONT="Courier New"]krandrtray[/FONT] from the command line and I was able to get my resolution changed to 1280x960, and I'm just living with that.

It's not the ideal solution, I know.  And the short answer is that I tried every solution I could find, including modding my xconf, runinng xfix from system boot, and so forth.

---

