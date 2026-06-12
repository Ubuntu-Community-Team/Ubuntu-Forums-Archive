---
title: "Google earth says video card on Optiplex 755 doesn't have 3D, direct9x support"
date: 2015-05-02
forum: Hardware
---

### Post by dora5 on 2015-05-02
I am having trouble installing Google Earth, and I am having trouble believing that the reason why is the exact error message I am getting.

I didn't have any trouble finding and installing Google Earth for Ubuntu from the Google Earth download page, but during installation it warned me that Google Earth might not work because my video card doesn't support DirectX 9, some kind of rendering and 3D and whatever.   And Google Earth won't even start.

I am running a Dell Optiplex 755, with onboard video.  I am running xubuntu.    Compositor is enabled in "Window Manager Tweaks".  Cairo dock works.   I also tried installing and starting Compiz; same error messages when I try to start Google Earth.

I just traded it with someone else for an Optiplex 745 that also had onboard video and ran Google Earth in Ubuntu with no trouble.    

This is a Core Duo 2.67 Ghz processor, and I'm having real trouble believing the system doesn't support directx 9 or 3 D and whatever.   How does it even play You tube without supporting 3d.  I kind of think not.

[COLOR=#000000][FONT=Tahoma][LEFT]The specific error message I last got when I tried to run Google Earth is:[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma][LEFT]
[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma][LEFT][LEFT][FONT=Segoe Print][COLOR=#010101]"Your graphics card does not meet the minimum spec required to run Google Earth, which is a 3D accelerated card with shader support.  [/COLOR][/FONT]
[FONT=Segoe Print][COLOR=#010101]
[/COLOR][/FONT]
[FONT=Segoe Print][COLOR=#010101]"Note:  If the loginstatus is blocking access to the OK button then click the login window, press Alt-F4, click on don't show this message again then click on OK button."[/COLOR][/FONT]
[FONT=Segoe Print][COLOR=#010101]
[/COLOR][/FONT]
[FONT=Segoe Print][COLOR=#010101]The Google support web site says the graphics card needs DirectX9 and 3D capable w 64 MB of VRAM.   [/COLOR][/FONT]
[/LEFT]
[/LEFT]
[/FONT][/COLOR]

I did alot of troubleshooting, results reported below.  But when I tried installing and trying to run Google Earth on my Mint installation on the same computer I ran into the same problem.   Mint allegedly has better driver support than Ubuntu, though I've yet to get anyone to support that statement, but Mint does do some thing differently and strangely.   But whatever the problem is it clearly is not specifically a product of all of the features that aren't included in Xubuntu.   

It turns out that upgrading the video card wouldn't even be simple since nearby Goodwill computerworks has only DVI-I connectors on the video cards it sells for under $40, and the only ones for under $40 that have the wrong connectors also are too big to fit on the machine (though it's a minitower - these are GIGANTIC cards, and you have to see the cooling systems Dell puts in its computers.)

The board would take a PCI-E card.

I have an extra PCI video card with 256 MB of RAM, that the specs say its 3D capability consists of directx 9, 2.0 opengl whatever, and all sorts of rendering.   This card was used in my 2004 Lenovo that died five years ago.   

This makes it seem even more unlikely that this Duo Core Dell machine's onboard video won't actually support directx 9 and 3D video.   

All I can get hardinfo to tell me is that the thing has absolutely no clue what the display does for OpenGL;  vendor, renderer, version all unknown, Direct Rendering No.   

Lists all sorts of "Extensions" and I don't see Directx or 3d among them.   If I'm supposed to see Directx or 3d among them.

This is bad news - not even my genealogy software will run without direct x (or Ubuntu imitation thereof), so that is even more reason to doubt this system won't even run directx 9.   (I know Linux really runs imitation directx9 in Wine, and some kind of substitute in its own drivers.)

The Dell web site does not tell me anything so specific as the video specifications on the bord.

The board is OGM819 - or 0GM819.   It appears to be an Optiplex 755 Motherboard 0GM819 JR271 Intel LGA 775.   Now, the Gigabyte 775 board I bought in 2010 that I'm running Windows on that supports everything I need it to runs everything video I need it to, and it's probably two years younger than the Dell board.   Once again I kind of don't think so.

Running lshw yield this information on my video;

there are evidently two onboard video processors and one is in use.

VGA compatible controller
82Q35 Express Integrated Graphics controller
Intel
id:2
pci@0000;00;02.0
versoin 02
width 32 bits
clock 33 MHz
compatibilities msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0

The 2nd display is UNCLAIMED, I figure because nothing is using it, and it has identical specs.   No driver, of course.

I am wondering if there is any chance there is an issue with what driver I am using and NOT with the onboard video not being able to do 3d, directx9, opengl, all sorts of rendering, light, dark and shader rendering, and all of that?   If so, how do I use the right drivers?   

Or it maybe that I need to install some support software (that may have been already loaded in the 745 because I was using Ubuntu gnome and not Xubuntu) to enable 3d support?   

I ran glxinfo, and it told me I DO have OpenGL.   

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R)Q35 x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 1-0.3.2
OpenGL Extensions - must be about 50 of them.
But it says things like GL_AMD_shader_trinary_minmax if shader support isn't there.

How come GLXINFO can find OpenGl and hardinfo says it is unknown and does not exist and its provider is unknown?-i

Also, I found a post that said I have  3d acceleration if the answer to the following is yes.

glxinfo | grep direct So, I ran glxinfo | grep direct and it gave me: 

direct rendering: Yes

So now why can't Google Earth find it.   Not to mention why can't hardinfo find it.   

Then I tried glxinfo | grep shader

GL 3DFX texture_compression FXTI, GL+AMD_shader_trinary_minmax,
GL_ARB_fragmentprogram
GL__ARB_Sampler_objects, LG_ARB_shading_language_100,  and etc .. looks like it does shader things to me.

So why the Google error?

In Mint, I ran /usr/lib/nux/unity_support_test -p, which surprised me by working, especially as the same command in Xubuntu gave me a directory not there error.  I thought perhaps it required having the Unity interface.   I got:

Not software rendered yes
not blacklisted yes
GLX fbconfig:  yes
GLX texture from pixmap:  yes
GL npot or rect tectures:  yes
GL vertex program yes
GL vertex buffer object yes
GL framebuffer object yes
GL version is 1.4+ yes
Unity 3d supported yes  - I don't know, does that mean it can run Unity 3d but not Google Earth?   My Optiplex 745, which could run Google Earth perfectly, could run Unity for almost 15 minutes without crashing.   

glxinfo -i : grep render, which runs in Mint without needing to have been installed, yields:

direct rendering:  No  (-i specified)
GLX_MESA multithread_makecurrent, GLX_MESA_qery_renderer
ditto
OpenGL renderer string:  Mesa DRI Intel(R) Q35 x86/MMX/SSE2

How come the same command in Xubuntu and Mint gave opposite answers?   In Xubuntu the answer was "Yes".  

Does "Not software rendered" yes mean "Software Is Rendered" No?  

GLX Spheres ran a perfect bunch of spinning multicolored circles, at 30.188476 to 451842 on the bunch of results I'm looking at.   


Since I installed and turned on compiz, sometimes, Google Earth still won't run, and sometimes it starts and runs, while still displaying the error message, but can't display the earth from space and can't display the geographical features.   So for instance you see a round blob of lines running among the stars, and if you get close up it will show you where Austin, Texas is but not the geography.  


Thanks!

---

