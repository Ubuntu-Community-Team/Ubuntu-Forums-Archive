---
title: "Games Really Slow"
date: 2008-08-17
forum: General Help
---

### Post by Unanimated on 2008-08-17
EDIT: Okay, nobody has been responding to this thread lately, so I'm just going to say that it's a direct rendering problem with my drivers (which it is) and see how many replies I get. I really need help with this. And please read the other posts before posting your comment.

EDIT2: Here's my current situation: I'm running kernel -21-generic, EnvyNG drivers won't install, and the proprietary drivers install but won't have direct rendering, no matter whether I use OpenGL or something else, all of my games run slowly.

My problem is that my games all run really slow. Granted, I only have Tremulous and Nexuiz, but here are my issues in each:

Tremulous - Slows waaay down whenever a human appears, or I go into the human base. Same for aliens.

Nexuiz - No weapon, no sound, no enemies, 6-7 fps.

I think it has something to do with my drivers. I have the proprietary drivers enabled, after I installed drivers using EnvyNG, and that made no difference at all. Help please?

---

### Post by Unanimated on 2008-08-17
bump

---

### Post by Unanimated on 2008-08-18
bump..

---

### Post by Unanimated on 2008-08-18
bump

---

### Post by timcredible on 2008-08-18
do you mean you installed an ati or nvidia driver a non-standard method?  the standard is to click on the icon on the top panel when it says you have a proprietary driver available.  if so, i would suggest uninstalling whatever you did and try it the standard way

---

### Post by Unanimated on 2008-08-18
I tried the proprietary drivers and drivers I got through EnvyNG. There was no difference whatsoever in performance. I'm using NVIDIA drivers.

---

### Post by Unanimated on 2008-08-18
bump

---

### Post by gjoellee on 2008-08-18
Nexuiz runs very bad for be as well, I think you shall just pass this one to the Nexiuz programmers

---

### Post by Unanimated on 2008-08-18
The thing is, I had to reconfigure my X server for something, and it was running perfectly before I did that.

---

### Post by Unanimated on 2008-08-18
bump

---

### Post by Unanimated on 2008-08-18
bump

---

### Post by Unanimated on 2008-08-19
bump

---

### Post by Unanimated on 2008-08-19
I updated the kernel earlier today, and it's running a little better, but not as good as I would like. Also, when I put all the graphics on High in Tremulous, which was fine before I had to reconfigure my X server (which I've done 4 times now), all the textures and lighting get messed up, so I have to put the graphics on low to get them back to normal.

---

### Post by colobix on 2008-08-19
It works fine and fast for me.
So I Guess the problems are because of your graphic card or wrong drivers installed.
Install Envy. It comes with most of new drivers.
If that doesn't work, maybe it's your graphic card.

---

### Post by Unanimated on 2008-08-19
Envy won't work since I updated my kernel. Again, the thing that bothers me is that it was working perfectly before I had to reconfigure my X server, and now it barely works.

---

### Post by colobix on 2008-08-19
Ok so remove your xserver and its settings folder and install it again.

---

### Post by Unanimated on 2008-08-19
How do I do that?

Also, since no one has asked me to put this in yet, here's my glxinfo output:

```
Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample
client glx vendor string: NVIDIA Corporation

```

---

### Post by Unanimated on 2008-08-19
bump

---

### Post by herteljt on 2008-08-20
> **Unanimated said:**
> 
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
[/CODE]

I don't have an Nvidia card, but I can tell you that Nezuiz needs direct rendering.  According to the code you posted this isn't the case.  


This error 

> Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.

is probably also causing you problems.  

I would suggest that you remove the drivers you installed using Envy and then install them via System > Administration > Hardware Drivers

Also, I'm not an expert on forum etiquette, but I would suggest holding yourself back on those bumps (you need to give people more than a few hours to respond to a post) :)

---

### Post by Unanimated on 2008-08-20
EDIT: It uninstalled those drivers fine, so it's installing the proprietary ones now. I'll see what happens after I reboot.

---

### Post by Unanimated on 2008-08-20
I'm using the proprietary drivers, but I get the same output.

Here's what I get when I install the driver version 96.43.05 through EnvyNG.

---

### Post by Unanimated on 2008-08-21
bump

---

### Post by Unanimated on 2008-08-21
bump

---

### Post by Unanimated on 2008-08-21
bump

---

### Post by Unanimated on 2008-08-21
bump

---

### Post by Unanimated on 2008-08-22
bump

---

### Post by Unanimated on 2008-08-22
bump

---

### Post by xeth_delta on 2008-08-22
From the screenshot you posted, I can see that you are still trying to use ENVY drivers. Have you tried the suggestion herteljt proposed? That is, using regular proprietary drivers.

After removing the ENVY drivers, you might need to reconfigure the X server.
```
sudo dpkg-reconfigure xserver-xorg
```
then install the other drivers

---

### Post by Unanimated on 2008-08-23
I did what you said, but I still get the same output when I type glxinfo | head. I am running kernel 2.6.24-21-generic, which came out a few days ago, so that might have something to do with it. I was running 2.6.24-19-generic before.

---

### Post by werries on 2008-08-23
Ok when you install the proprietary nvidia drivers it actually replaces part of xorg. So reconfiguring will reset that and make things screw up again. I say reinstall the envy ng drivers.

---

### Post by Unanimated on 2008-08-23
When I use Envy, the result shown in the image above happens every single time. The proprietary drivers are the only ones that actually work.

---

### Post by xeth_delta on 2008-08-23
> **werries said:**
> Ok when you install the proprietary nvidia drivers it actually replaces part of xorg. So reconfiguring will reset that and make things screw up again. I say reinstall the envy ng drivers.

That is true, and that is why it has been recommended to him to do that before reinstalling.

---

### Post by xeth_delta on 2008-08-23
> **Unanimated said:**
> I did what you said, but I still get the same output when I type glxinfo | head. I am running kernel 2.6.24-21-generic, which came out a few days ago, so that might have something to do with it. I was running 2.6.24-19-generic before.

That might be the case. Whenever there is a new kernel installed, the interface between it and the driver has to be one that is appropiate for that specific kernel.

> **Unanimated said:**
> 
When I use Envy, the result shown in the image above happens every single time. The proprietary drivers are the only ones that actually work.


I am a bit confused by what you say here. Are the regular proprietary drivers working? Please check in both driver cases if you have direct rendering
```
glxinfo | grep -i direct
glxinfo | grep -i opengl
```

---

### Post by Unanimated on 2008-08-23
By that I mean that the proprietary ones are the only ones that will install and work. The Envy ones don't install.

Here's my direct output:

```
Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

And my opengl output:

```
Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 Ti 4200/AGP/SSE/3DNOW!
OpenGL version string: 1.5.8 NVIDIA 96.43.07
OpenGL extensions:

```

---

### Post by xeth_delta on 2008-08-23
The line stating
```
direct rendering: No
```
is a clear sign that something's wrong with those drivers. If the regular proprietary drivers work, why not use them?

---

### Post by Unanimated on 2008-08-23
I was using them when I posted the results to those commands, and I still am using them. When I said "work" I meant they install.

---

### Post by stoneage on 2008-08-23
Is that kernel the one Intrepid uses? I read somewhere there were drivers problems with it.

EDIT - It was xorg and drivers - [http://www.ubuntu.com/testing/intrepid/alpha2](http://www.ubuntu.com/testing/intrepid/alpha2)

---

### Post by Unanimated on 2008-08-24
So.. what should I do?

Also, Intrepid uses -26, not -21.

---

### Post by GenesisV2.0 on 2008-08-24
hi - recently learned some stuff like this while playing with wine - have you tried using opengl??

---

### Post by Unanimated on 2008-08-24
The same thing happens - no direct rendering.

---

### Post by Unanimated on 2008-08-24
bump

---

### Post by Unanimated on 2008-08-25
bump

---

### Post by maxmanapple on 2008-08-25
> **Unanimated said:**
> EDIT: Okay, nobody has been responding to this thread lately, so I'm just going to say that it's a direct rendering problem with my drivers (which it is) and see how many replies I get. I really need help with this. And please read the other posts before posting your comment.

EDIT2: Here's my current situation: I'm running kernel -21-generic, EnvyNG drivers won't install, and the proprietary drivers install but won't have direct rendering, no matter whether I use OpenGL or something else, all of my games run slowly.

My problem is that my games all run really slow. Granted, I only have Tremulous and Nexuiz, but here are my issues in each:

Tremulous - Slows waaay down whenever a human appears, or I go into the human base. Same for aliens.

Nexuiz - No weapon, no sound, no enemies, 6-7 fps.

I think it has something to do with my drivers. I have the proprietary drivers enabled, after I installed drivers using EnvyNG, and that made no difference at all. Help please?

a) Tremulous has linux version. Give it a try
b) Install general driver fglrx

If any of those didn't help, maybe your problem must be seen by advanced user

---

### Post by Unanimated on 2008-08-25
> **maxmanapple said:**
> a) Tremulous has linux version. Give it a try
b) Install general driver fglrx

If any of those didn't help, maybe your problem must be seen by advanced user
I'm running the Linux version of Tremulous, and fglrx is already installed.

---

### Post by Crafty Kisses on 2008-08-25
While playing, post the results of this command > top

---

