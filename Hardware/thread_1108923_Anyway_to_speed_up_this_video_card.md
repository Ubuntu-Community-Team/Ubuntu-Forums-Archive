---
title: "Anyway to speed up this video card?"
date: 2009-03-28
forum: Hardware
---

### Post by zeroandone on 2009-03-28
The video card on my laptop is this:
ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

I know it is old and when I surf websites with Flash videos, my laptop fan just runs forever. But when I run Windows I don't have this problem. Is it caused by the video card? If yes, is there any way to improve it?

---

### Post by zeroandone on 2009-03-30
Anyone please?

Thanks,

---

### Post by Big_Croc7 on 2009-03-30
the problem probably isn't with your video card - it's with flash. the official linux version of flash (from adobe) is rubbish, and runs slowly on most computers. the reason, i think, is because adobe don't care about linux support, and try to stop anyone else producing a version of flash that works. unfortunately, there isn't a reliable way to solve this issue at the moment.

there are a number of things you could try, but the chance of success is probably slim. you could try replacing the adobe flash player with one of the open source versions (either swfdec or gnash, for example), but the last time i checked they were quite far behind and a lot of sites use newer features that they don't support (edit: this was quite a while ago, so they may be worth looking at now). if you can download the actual file you can play it in mplayer, for example - this works well, but it's more hassle. updating your graphics card drivers etc probably won't help (though you could try) ao it's probably a software rendering problem (i.e. the cpu has too much to do, not the graphics card).

edit 2: it's easy to get mixed up with this. flash files can be either swf or flv, i think swf is vector grapics and flv is videos, and each has different requirements. i can't remember the details - have a hunt round the web before installing anything.

---

### Post by zeroandone on 2009-03-30
> **Big_Croc7 said:**
> the problem probably isn't with your video card - it's with flash. the official linux version of flash (from adobe) is rubbish, and runs slowly on most computers. the reason, i think, is because adobe don't care about linux support, and try to stop anyone else producing a version of flash that works. unfortunately, there isn't a reliable way to solve this issue at the moment.

there are a number of things you could try, but the chance of success is probably slim. you could try replacing the adobe flash player with one of the open source versions (either swfdec or gnash, for example), but the last time i checked they were quite far behind and a lot of sites use newer features that they don't support (edit: this was quite a while ago, so they may be worth looking at now). if you can download the actual file you can play it in mplayer, for example - this works well, but it's more hassle. updating your graphics card drivers etc probably won't help (though you could try) ao it's probably a software rendering problem (i.e. the cpu has too much to do, not the graphics card).
Thank you for the reply. It makes sense now. I am using Adobe flash player and it not only runs slow but also causes my computer to shut down by itself because of the overheat of the CPU, very frustrating. I will give those open source driver a try to see how it goes.

---

### Post by 20vturbodub on 2009-03-30
Can you let us know how that works out for you. I am having the same issue with my dell laptop. About 5 minutes into a flash video the fan comes on and my laptop starts pumping out some serious heat. I always thought that it was due to the processor my laptop uses. It is an older Inspiron 5100 with a P4 2.33 ghz desktop chip.

---

### Post by Big_Croc7 on 2009-03-30
yes, do let us know if it works. if it's youtube you're after my prefered method is pause the video, wait till it's all loaded and then:
cd /tmp
ls | grep 'Flash'
mplayer Flash??????

where ??? is a string of letters/numbers. plays fullsceen, even on a 10 year old machine!

iplayer is more difficult as it doesn't buffer the stream, but can be done too without much trouble apparently - i haven't tried.

---

### Post by zeroandone on 2009-03-30
I will definitely let you know how it works, but now I am not home and cannot test it. Will do after I get off work today.

---

### Post by zeroandone on 2009-04-03
> **Big_Croc7 said:**
> yes, do let us know if it works. if it's youtube you're after my prefered method is pause the video, wait till it's all loaded and then:
cd /tmp
ls | grep 'Flash'
mplayer Flash??????

where ??? is a string of letters/numbers. plays fullsceen, even on a 10 year old machine!

iplayer is more difficult as it doesn't buffer the stream, but can be done too without much trouble apparently - i haven't tried.
Here is an update of my problem.
I uninstalled flashplugin-nofree and tried swfdec and gnash, but they didn't work very well. When I went to sites with flash, the flash didn't play at all.
I also tried the command you specified in your post, and I didn't see any file with "Flash" in it.
So I ended up with reinsalling flashplugin-nofree package from Synaptic in order to play flash.
So, problem still exists.

---

### Post by Big_Croc7 on 2009-04-06
Hmm.  I've just tried swfdec (aptitude install swfdec-mozilla), and it works for me with Youtube (though still takes up quite a lot of cpu).

Sorry if I was unclear about those commands - they're if you have a plugin installed.  You'll have to wait for the plugin (e.g. the Adobe player) to buffer the whole video, and them grab it from the tmp folder.  You still need a plugin, and you'll have to wait for the whole thing to download before watching it, but at least then you should be able to watch it without stuttering etc.

---

### Post by Skara Brae on 2009-04-06
Well, only yesterday I have installed Xubuntu 8.04 on a(n ancient) Compaq Armada E500: a PIII 500 mhz, 2 x 128 MB RAM and the same Ati Rage Mobility video'card'.

Flash works (relatively) fine here, though, like on Youtube. Or like on:
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

EDIT: And right after closing the tab with the Adobe webpage while typing this, Firefox "hung" and I had to "kill" it, making me lose the text I was typing.

EDIT: Now, the second time, Firefox keeps on going.

Could it be because I have Xubuntu installed, which is supposed to be easier than Ubuntu/Kubuntu (so I read)?

---

### Post by Kangarooo on 2009-04-11
To know if your video card is installed you need to go to Hardware Drivers and see it there..
Is this correct?
And the more faster or bigger or many objects are in flash the more CPU it needs and GraphicCard also

---

### Post by Kangarooo on 2010-06-02
Actually CPU also i used for Flash a lot so better CPU->better flash

---

