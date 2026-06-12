---
title: "17&quot; widescreen resolution fix messed up rest of applications, now can't use Terminal"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by peacechicken on 2007-04-27
I'm using a Hanns-G 17" widescreen LCD and GeForce 7300 video card. In the process of trying to fix the resolution (so it would be the recommended 1440x900) I used directions from this page: [http://www.bi03.co.uk/home/blog.php?id=8](http://www.bi03.co.uk/home/blog.php?id=8)
which had me use Terminal to reconfigure settings using "sudo dpkg-reconfigure xserver-xorg"

I went through all of the steps, using recommended or default settings for most questions, and when it finished, the 1440x900 was finally an option in the pull-down Screen Resolution menu. It looked great, I thought it was fixed. But then I noticed when I open any application, I'm unable to move or resize any windows and they've also lost their normal "look", like the chrome is gone. I'm attaching a screenshot of what Terminal looks like for me now.

Some applications still function, like Firefox. But when I open Terminal, I get a white screen with no interface and I'm not able to input anything. Which pretty much limits me in trying to follow any recommended fixes because everything I've found involves using Terminal.

What are my options now? Let me know what further details anyone would need in troubleshooting this, I'll give everything I can. Please keep in mind I'm only a novice Ubuntu user right now.

Thanks so much!

---

### Post by Seq on 2007-04-27
Press Alt + F2 to get a run dialog, and run "metacity" (lowercase, without the quotes). That should get your WM back. If metacity does not restart when you log out and back in, then it will need to be added to your session. Post back if it does not.

Also, the terminal is active, it is just hidden under the panel. If you press return a few times, you will see the prompt.

---

### Post by peacechicken on 2007-04-27
I did that, a couple times, nothing changed.

Next steps?

---

### Post by peacechicken on 2007-04-27
Through some more searching I came upon this post and it worked perfectly for me:
[http://ubuntuforums.org/showthread.php?t=415142](http://ubuntuforums.org/showthread.php?t=415142)

Here was the solution:
> Simple fix for nvidia users. Just reconfigure the x.org config.

run

sudo nvidia-xconfig --add-argb-glx-visuals

It'll back up your current xorg.conf, and create a new one. Just restart X with ctrl+alt+backspace or reboot and your good to go!



Thank you Seq, I appreciate your help!

---

