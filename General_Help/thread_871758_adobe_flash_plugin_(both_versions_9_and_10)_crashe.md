---
title: "adobe flash plugin (both versions 9 and 10) crashes in firefox"
date: 2008-07-27
forum: General Help
---

### Post by ireneshusband on 2008-07-27
I have a serious problem with flash crashing within firefox. I know there are a lot of reports on launchpad of various versions of this problem (so many that I can no longer make sense of them all), but AFAIK none of these accurately describe my problem.

I run flash within firefox 3 on amd64 hardy, using nspluginwrapper. What happens is that whenever I load a flash object, there is a good chance the plugin will crash, taking all the already loaded flash objects with it and requiring that firefox be restarted to get the plugin working again.

There is a very long discussion on launchpad that was originally about a report to do with problems with sound output using pulseaudio, but I don't seem to have any audio problems as such, and in any case, audio-free flash objects seem just as likely to crash the plugin as ones that make noise. Unlike with Skype, which I had route separately through dmix to get it working, flash seems to be able to use pulseaudio no problem.

One suggestion I did follow from that discussion was to remove libflashsupport, and for a while this seemed to work, in that the crashes were quite infrequent. But now the problem has returned with a vengeance. And just to be clear, this is a Firefox problem. It doesn't seem to occur in Opera (which is not to say that flash in Opera never crashes).

Another bug report I came across (which I cannot for the life of me locate at the moment) talked a lot about problems very like mine happening using Flash 10 and suggested rolling back to 9, which apparently doesn't have the same problems. But when I went to roll back to 9 I found out that that was the version that was already installed.

So I've just tried *up*grading to 10 (from archives.ubuntu.org), but the problem seems to be as bad as ever.

Unfortunately the Ubuntu devs (and I hope they will forgive me for being so blunt about this) don't seem to have understood that if the web browser, the single most important desktop application, either cannot display the most widely accessed web content at all, or else renders it only semi-legibly underneath a layer of blank grey rectangles, then the operating system is not fit for normal desktop use. In the meantime I am torn between trying to carry on with firefox, which in other ways has done me well and which I am used to, or deserting it for Opera, which is a great browser, but not quite what I need.

So I guess I have two questions:
[LIST=1]
[*]Am I alone in having this particular problem? Is it really a bit different from the problems other users are experiencing with flash?
[*]Does anyone know a workaround?
[/LIST]

---

### Post by markbuntu on 2008-07-27
Well, first of all, you need the nspluginwrapper for flash if you are using amd64. The other thing is that flash10b works but flash10b2 does not and of course flash9 does not work. If you can find flash10b or 10b1 use that.

I have had zero crashes with flash since getting flash10b abd getting rid of libflashsupport.

---

### Post by ireneshusband on 2008-07-28
Thank you!

But does anyone actually know how to get hold of flash 10b? I'm not having much luck :(

---

