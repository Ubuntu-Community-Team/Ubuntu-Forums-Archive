---
title: "dual monitor with my HDTV"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by linksolo74 on 2008-01-22
I really want to get my HDTV to work with Ubuntu. I cannot get it to work for the life of me though! I go into screens and graphics and it won't let it be my second monitor. It works fine on windows (this is one of the main reasons i am still using windows other then games.). I have a 2002 sony 51' projection HDTV connected through my s-video port. help please..... oh and i am using a ATI radeon 9600 graphic card.

PS: i just want to use it for watching videos on my HDTV.

---

### Post by linksolo74 on 2008-01-23
help.....anyone??????

---

### Post by linksolo74 on 2008-01-26
bump

---

### Post by chewearn on 2008-01-26
Rather than S-video, can you use VGA instead?  Unless the hardware doesn't support it.

---

### Post by linksolo74 on 2008-01-26
VGA? No. My HDTV doesn't support VGA, or rather it doesn't have a VGA input. Plus i only have one VGA port on my Graphic card, which i am using for my monitor. I do have DVI port on my Card and my TV though. Would that help?

---

### Post by merobertd on 2008-01-26
hi 
i don't know if this will help but i got my hd tv kind of working by typing "nvidia-settings" in the terminal and playing around with that, but it might be different for ATI cards try "ATI-settings"
rob

---

### Post by linksolo74 on 2008-01-26
nothing happens if i type "ATI-settings" in the terminal. If i type "nvidia settings" i get

The program 'nvidia-settings' can be found in the following packages:
 * nvidia-glx
 * nvidia-settings
 * nvidia-glx-new
Try: sudo apt-get install <selected package>
bash: nvidia-settings: command not found


Now if i were to install nvidia and use that to change stuff would it really mess stuff up or would it just not work? sorry i'm a NOOb.

---

### Post by merobertd on 2008-01-26
if you have an ati card the nvidia driver won't do anything for you. have to got the restricted driver enabled if not enable it. that should get you the driver you need. the "nvidia-setting" worked for me cause i have an nvidia card.

"sudo aticonfig" might get you a dialog box like the one from windows that should let you use it. 
if it dosent im stumped. im a bit of a newbie to.

---

### Post by linksolo74 on 2008-01-26
okay so i tried the restricted driver, and it just made me run my computer in low-graphic mode until i disabled it.
then i installed the ATI binary X.Org driver. and went into the terminal and entered "sudo aticonfig" and i got this:


Usage: aticonfig [OPTION] ...
Parses an existing X-Server configuration file and modifies it to operate with
ATI products.

The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
           NTSC-M 
           NTSC-JPN
           NTSC-N
           PAL-B
           PAL-COMB-N
           PAL-D
           PAL-G
           PAL-H
           PAL-I
           PAL-K
           PAL-K1
           PAL-L
           PAL-M
           PAL-N
           PAL-SECAM-D
           PAL-SECAM-K
           PAL-SECAM-K1
           PAL-SECAM-L
        Note: Not all graphics cards support every mode. Regional 
              settings are applicable. 
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV
 --tv-overscan={on|off}
       Enable or disable overscan mode for TVout
       Note, not all tv-formats support overscan. Try to 
       toggle overscan off before changing tv-format if 
       and error occurs. 
 --tv-info
         Print out the current tv geometry, tv format, and if the
         tv is physically connected. 
 --tv-geometry=WIDTHxHEIGHT{+|-}X{+|-}Y
              =WIDTHxHEIGHT
         Change the size and position of the TVout display. 
         WIDTH and HEIGHT are in percentage units. Please note
         that the valid range for WIDTH and HEIGHT depends on
         the tv-format selected. However, as a rule of thumb  
         WIDTH and HEIGHT are valid in the range [1,100]  
         X and Y are pixels offsets from centre 
         of the screen. X and Y are have variable ranges dependant 
         on ASIC. Use tv-info to get valid X and Y ranges 
         If tv-geometry is invoked with just width and height 
         then X and Y are assumed to be 0
         See example 5 below for a sample usage. 

FireGL Workstation Board Features:
  --app, --use-app-profile=STRING
        Change the application profile for a FireGL workstation board.
        STRING can be one of:
            default
            maya
            softimage-xsi
            softimage-3d
            houdini4.0
            houdini5.0
            houdini5.5
FSAA Options:
  --fsaa={on|off}
        Enable/disable full scene anti-aliasing.  Enable this option to enhance
        photo-realism in 3D rendering.  Disable it to get the most accurate 3D
        image.
  --fs, --fsaa-samples={off,0,2,4,6}
        Set the number of FSAA samples per pixel or 2, 4, 6.  off is the same
        as setting 0 samples.
  --fsg, --fsaa-gamma={on|off}
        Enable/disable FSAA gamma.
  --fmsp, --fsaa-ms-positions=x0,y0,x1,y1,x2,y2,x3,y3,x4,y4,x5,y5
        Change the FSAA Multi-Sample Positions for x0,y0 to x5,y5.  You must
        specify exactly 12 real number values separated by commas.

Screen-Related Options:
  --ovt, --overlay-type=STRING
        Change the overlay for the X server.  STRING can be one of:
            opengl
            Xv
            disable
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
        or stereo.
  --lcd, --lcd-mode=STRING
        Change the LCD mode.  STRING can be one of:
            center
            full
  --dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
                                Note: This option is NOT supported with Avivo
            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
            horizontal          2 screens - one framebuffer,
                                screen 1 right of screen 0
            horizontal,reverse  2 screens - one framebuffer,
                                screen 1 left of screen 0
            vertical            2 screens - one framebuffer,
                                screen 1 above of screen 0
            vertical,reverse    2 screens - one framebuffer,
                                screen 1 below of screen 0
        Note:  This option is not valid if '--initial=dual-head' is specified.
  --vs, --sync-vsync={on|off}
        Enable/disable sync buffer swaps with vsync.  Enable this option to
        prevent tearing during 3D rendering.
  --psc, --pseudo-color={on|off}
        Enable/disable pseudo-color visuals.  Enable this option to get 16-bit
        color support.
  --stereo={on|off}
        Enable/disable quad-buffer stereo support.  Enable this option only for
        using applications that support the use of hardware 3D shutter glasses.
  --ss, --stereo-sync={on|off}
        Enable/disable quad-buffer stereo sync.  Enable this option to get 3D
        glasses to synchronize with the infrared transmitter.
  --resolution=Screen#,W1xH1,W2xH2,W3xH3,...
        Set the modes for the specified screen.  You may specify several
        resolutions separated by commas.
        Screens start at 0.  You can use 1 for dual-head
  --hsync=Screen#,LOW-HIGH
        Change the horizontal sync range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --vrefresh=Screen#,LOW-HIGH
        Change the vertical refresh range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --hsync2=LOW-HIGH
        Change the horizontal sync range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --vrefresh2=LOW-HIGH
        Change the vertical refresh range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --mode2=W1xH1,W2XH2,W3xH3,...
        Change the modes for the second display.  You may specify several
        resolutions separated by commas.  Only valid for clone and big desktop
        settings.
  --screen-layout={left|right|above|below}
        Set the secondary screen position for dual head.
  --screen-overlap=NUM
        Set the screen overlap region in big desktop mode to be NUM pixels.
  --force-monitor=STRING[,STRING...]
        Describe all displays that are to be enabled and/or disabled regardless
        of physical connection.  STRING can be one or more of the following
        set, separated by commas:
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            tmds2i
            nocrt1
            nocrt2
            nolvds
            notv
            notmds1
            notmds2
            notmds2i

POWERplay Options:
  Following options will not change the config file. 
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --lsp, --list-powerstates
        Print information about power states and exit.
  --set-powerstate=NUMBER
        Set a power state listed by --list-powerstates.

Advanced Options:
  --sync-video
        Enable/disable sync to vsync for AVIVO video.
        This option is enabled by default and is used to prevent
        video tearing. By disabling this option video is free to
        render as fast as the 3D engine can handle. In the case of
        choppy video try to disable sync-video.
  --tls={on|off}
        Enable/disable fast thread local storage.  Disable this option when
        virtual machines or WineX fail to work properly.
  --sb, --signal-block={on|off}
        Enable/disable signal blocking.  Disable this option when debugging a
        multi-threaded OpenGL application.
  --locked-userpages={on|off}
        Enable/disable locked user pages. Disable this option if the system
        hangs when running fgl_glxgears.
        User page lock is no longer available on AGP system now.
  --gcpu, --generic-cpu={on|off}
        Enable/disable generic CPU.  Use this option if the CPU is being
        reported improperly.  For example: If you have an AMD cpu that is
        being reported as Intel.
  --max-gart-size=NUMBER
        Set user-defined max GART size for non-AGP systems.
        Possible integer values are from 64 to 512 (mb).

Dynamic Display Management Options:
  Following options will not change the config file. They are
  used for querying driver, controller and adaptor information.
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --enable-monitor=STRING,STRING
        Setting current monitor to be enabled. Only 2 displays
        can be enabled at the same time. Any displays
        that are not on the list will be disabled.
        STRING can be one of the following set, separated 
        by commas:
            none
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            auto   -- use default policy to enable the displays.
  --query-monitor
        This will return connected and enabled monitor information
  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.
  --swap-screens={on|off}
        Enable/disable swap heads in dual-head mode.
        This option works only in dual-head mode.

Pair mode options: 
  Following options are used for query add and remove pair modes. 
  These options will be effective immediately. Other options on   
  the same command line will be ignored.
  --list-pairmode 
        list all the current existing pair modes the driver can use.
  --add-pairmode=width0xheight0+width1xheight1
        Add one pair mode to the list. width0 and height0 are the 
        size of primary display and width1 and height1 for the 
        secondary  display.
  --remove-pairmode=index 
        Remove one pair mode from the list. User can get index by 
        list-pairmode.

External Events Daemon Options:
  Following options will not change the config file. They are
  used to send commands to the atieventsd external events daemon.
  --set-policy=STRING
        Sets the event policy for the daemon to be STRING.
        See the atieventsd(8) manpage for further details.

Miscellaneous Options:
  -v, --verbose
        Show what aticonfig is doing.
  -q, --quiet
        Disable all information output except for errors.
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  --nobackup
        Do not make an automatic backup of the configuration file.
  -i, --input=FILE
        Select a FILE to input as the configuration file. Set FILE to '-' to
        pipe from standard input.  Without this option, aticonfig will search
        /etc/X11 for the default configuration file.
  -o, --output=FILE
        Select a FILE to output the new configuration file to.  Set FILE to '-'
        to print to standard output.  Without this option, aticonfig will
        replace the input file with the newly generated file.
  -h, --help
        Display this help screen.
  -f, --force
        Only valid with 'initial' option.  Force aticonfig to generate default
        Monitor, Device, and Screen sections even if the original configuration
        file has invalid settings in these sections.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768
  4. Force primary CRT on and TV-out off.
                        aticonfig --force-monitor=crt1,notv
  5. Change tv geometry 
                         aticonfig --tv-geometry=85x90+10-10 
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre. 

Please report bugs to [http://support.ati.com](http://support.ati.com)

well after that i thought the best thing to do would be to enter "sudo aticonfig enable-monitor=crt1,tv" (i use a CRT monitor).

well after that i got:



aticonfig: Writing to '/etc/X11/xorg.conf' failed. No such file or directory.
No ATI fglrx device was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' or change the 'Driver' part of your configuration
file to "fglrx" and run aticonfig again.


so i did "aticonfig --initial" and it said this


Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfe82a2a ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d6192b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d0a050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 16:01 2687278    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 16:01 2687278    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7ce6000-b7ce7000 rw-p b7ce6000 00:00 0 
b7ce7000-b7ce9000 r-xp 00000000 16:01 3818446    /lib/tls/i686/cmov/libdl-2.6.1.so
b7ce9000-b7ceb000 rw-p 00001000 16:01 3818446    /lib/tls/i686/cmov/libdl-2.6.1.so
b7ceb000-b7cef000 r-xp 00000000 16:01 820531     /usr/lib/libXdmcp.so.6.0.0
b7cef000-b7cf0000 rw-p 00003000 16:01 820531     /usr/lib/libXdmcp.so.6.0.0
b7cf0000-b7cf2000 r-xp 00000000 16:01 820520     /usr/lib/libXau.so.6.0.0
b7cf2000-b7cf3000 rw-p 00001000 16:01 820520     /usr/lib/libXau.so.6.0.0
b7cf3000-b7cf4000 rw-p b7cf3000 00:00 0 
b7cf4000-b7e38000 r-xp 00000000 16:01 3818443    /lib/tls/i686/cmov/libc-2.6.1.so
b7e38000-b7e39000 r--p 00143000 16:01 3818443    /lib/tls/i686/cmov/libc-2.6.1.so
b7e39000-b7e3b000 rw-p 00144000 16:01 3818443    /lib/tls/i686/cmov/libc-2.6.1.so
b7e3b000-b7e3e000 rw-p b7e3b000 00:00 0 
b7e3e000-b7e61000 r-xp 00000000 16:01 3818447    /lib/tls/i686/cmov/libm-2.6.1.so
b7e61000-b7e63000 rw-p 00023000 16:01 3818447    /lib/tls/i686/cmov/libm-2.6.1.so
b7e63000-b7f50000 r-xp 00000000 16:01 820514     /usr/lib/libX11.so.6.2.0
b7f50000-b7f54000 rw-p 000ed000 16:01 820514     /usr/lib/libX11.so.6.2.0
b7f54000-b7f61000 r-xp 00000000 16:01 820535     /usr/lib/libXext.so.6.4.0
b7f61000-b7f62000 rw-p 0000d000 16:01 820535     /usr/lib/libXext.so.6.4.0
b7f62000-b7f69000 r-xp 00000000 16:01 820557     /usr/lib/libXrender.so.1.3.0
b7f69000-b7f6a000 rw-p 00006000 16:01 820557     /usr/lib/libXrender.so.1.3.0
b7f6a000-b7f6f000 r-xp 00000000 16:01 820555     /usr/lib/libXrandr.so.2.1.0
b7f6f000-b7f70000 rw-p 00005000 16:01 820555     /usr/lib/libXrandr.so.2.1.0
b7f70000-b7f71000 rw-p b7f70000 00:00 0 
b7f76000-b7f80000 r-xp 00000000 16:01 3784771    /lib/libgcc_s.so.1
b7f80000-b7f81000 rw-p 0000a000 16:01 3784771    /lib/libgcc_s.so.1
b7f81000-b7f83000 rw-p b7f81000 00:00 0 
b7f83000-b7f9d000 r-xp 00000000 16:01 3784717    /lib/ld-2.6.1.so
b7f9d000-b7f9f000 rw-p 00019000 16:01 3784717    /lib/ld-2.6.1.so
bfe6e000-bfe84000 rw-p bfe6e000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


anyone know what to do about this? And thanks for all the help you have given me so far.

---

### Post by chewearn on 2008-01-26
> **linksolo74 said:**
> VGA? No. My HDTV doesn't support VGA, or rather it doesn't have a VGA input. Plus i only have one VGA port on my Graphic card, which i am using for my monitor. I do have DVI port on my Card and my TV though. Would that help?

DVI is also good.  It will anyway gives significantly higher resolution than S-video.  I'm not sure about solving your other problem with ati driver, though.

---

### Post by merobertd on 2008-01-27
I have no idea what to do sorry
rob

---

