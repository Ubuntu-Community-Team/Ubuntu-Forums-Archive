---
title: "fullscreen/geometry issues with gnome-terminal and multiple monitors"
date: 2008-07-30
forum: General Help
---

### Post by Xnyper on 2008-07-30
My setup:

Two monitors, one rotated 90 degrees (so that what was a widescreen monitor is now a tallscreen monitor).  That rotation is a line I put in xorg.conf

nVidia drivers running these monitors together with Xinerama, I can play with them using nvidia-settings.

My wants:

I would like to run a gnome-terminal in the tall screen and have the window be either fullscreen or close to fullscreen.  I want to figure out the right syntax so that I can put it in a shortcut on the panel, rather than running the program and dragging the window edges with my mouse.

Maybe this is a lot of work to avoid clicking the maximize button each time, but darnit I want it my way.

note about Xinerama: 

when I click a link on my tall monitor, the window opens in the tall monitor.  When I click a link on the standard one, the window opens there.  For some reason, when a window opens maximized, it will sometimes pop over to the standard display (gnome-terminal, firefox) but will sometimes open in the tall display like it's supposed to (oowriter).

note about my profile: 
the profile "terminal" is nothing too special, I just changed some colors and removed the scrollbar.

My story:

I found that when I run the command:
```
gnome-terminal --full-screen --window-with-profile-internal-id=terminal
```
the window pops over to the standard display, and correctly fullscreens itself.

I found that when I run the command:
```
gnome-terminal --geometry=127x**y** --window-with-profile-internal-id=terminal

``` where **y** is a number less than or equal to 56.
The window opens on the tall screen (which is good) but does not extend far enough downward.  Variations in **y** modify the window size as they should.  

I found that when I run the command:
```
gnome-terminal --geometry=127x**Y** --window-with-profile-internal-id=terminal

``` where **Y** is a number greater than 56.
The window opens on the tall screen, but regardless of the value I put in for **Y**, it opens with a height of 56.  After some window resizing I found out that the dimensions I am looking for are 127x72, but when these dimensions are chosen the resulting window is 127x56.

I know the setup is capable of displaying the window with my target dimensions, it does so if I open a small gnome-terminal and resize the window with my mouse, but fails whenever I try to get the window to open that way.

Thanks for helping me out!

---

