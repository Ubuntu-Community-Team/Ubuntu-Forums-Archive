---
title: "AWN - Twinview configuration help"
date: 2008-10-09
forum: General Help
---

### Post by ZManODS on 2008-10-09
I am running Hardy Heron and I installed AWN which looks great.

The only problem is when I am running a dual monitor setup I can not get the AWN toolbar on the right (right as in the monitor on the right) monitor.

Is there anyway I can manually configure on what monitor the toolbar should show up on?

FYI My video card is a NVIDIA 6800

---

### Post by loomsen on 2008-10-10
Yep, there is. I have two separate Xscreens tho, but I dont think this should be of interest.

Here we go, first lets find out how your displays are named.

```
glxinfo | grep screen
```
tells me:
```
docter@doc-laptop:~$ glxinfo | grep screen
display: :0  screen: 0
display: :0  screen: 1

``` 

So my first screen is named 0.0. and my 2nd one is 0.1.

Now, to start an app on a specified screen, type:
```

DISPLAY=:0.1 foo_bar

```
what would make a app foo_bar start on my TV. Actually I created an alias in my bashrc, so that I don't have to type DISPLAY=:0.1, but 
TV foo_bar
will do the same.(So my alias is obv specified as: 
alias TV='DISPLAY=:0.1'
)

should work for you as well I think, but with twinview you wont get compiz running, if you're after that too. 

Taking screenshots makes clear why this is not possible.

Let's take a look at the different modes:
1. TwinView: stretches your desktop over two screens, should work without a problem if both screens have the same resolution. 
Assuming lets say two screens with 1500 pix width and 900 heighth, side by side, TwinView would give you one big virtual desktop, with the virtual size 
3000x900. That should make clear why compiz won't work, rotating the cube for example isn't even imaginable.

2. Now, if you have to handle different resolutions, that is a lil bit more of a problem.. 
       a) with Xinerama: you'd be able to drag windows from one screen to other and back. Compiz won't work here neither, cause it would try to keep the dragged window on the current screen, by rotating the cube.
       b) without Xinerama: which is the best way to configure your X in my eyes. Gives you two separate Xscreens, everyone independently configurable, and each providing full resolution. You are not able to drag windows back and forth in this case, tho you are able to move your mouse whereever you want. Just the windows remain where they were started. You can drag icons tho. Anyway, this will enable compiz as well, so imho the only reasonable thing to achieve.


You may find [THIS THREAD](http://ubuntuforums.org/showthread.php?t=942946) useful as well, I posted my xorg.conf there.

Hope this helped you, good luck achieving your goals.

Tho, I just cant withstand, forget AWN ;)

---

### Post by ZManODS on 2008-10-13
thanks for the reply.

You actually brought up an issue I am seeing. If I change my display to use twinview with nvidia-settings then I will get one big desktop with one long gnome panel. Also if I maximize a window it will stretch across both screens. This is not the desired behavior I am looking for.

However if i restart my computer with the same twinview settings I will get the gnome panel and maximized windows across only one screen which is the behavior I want. 

Do you know why this is happening or what setting I can change to fix this?

thanks.

---

