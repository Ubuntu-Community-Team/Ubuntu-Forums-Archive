---
title: "Grub hangs up during startup"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Ouguiya on 2009-05-05
Hello everybody!

I have recently installed ubuntu for a friend of mine, but things just don't seem to work.

At first, we chose to install ubuntu on the entire hard drive. We let ubuntu do everything automatically.

After installation, everything first went fine. We started into ubuntu, installed the newest updates, and lots of stuff.

We restarted once again after that, and still, all worked fine, so I took my leave on my friend.

Now, my friend called me back, telling me that booting just resulted in Grub saying: "Grub loading stage 1.5", and a blinking cursor just beneath it, but nothing happening else.

I have looked around for a long time, but haven't found any good solutions. In most cases, Grub says "Please wait", but in this case, Grub doesn't even say that phrase.

First, I advised my friend to change some boot options, as was recommended by some other sites where users reported this problem, but this did not work either.

Also, powering the laptop on and off didn't work either (3 times).

I hope somebody has a solution for this, as reinstalling the entire ubuntu and all packages would be quite bothersome.

Thanks in advance,

Yours,

Ouguiya

---

### Post by caljohnsmith on 2009-05-05
In order to get a clearer picture of your friend's setup related to his booting problem, how about having him download the **Boot Info Script** to his Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely his Ubuntu desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your friend's setup and hopefully what the solution to his booting problem might be.

John

---

