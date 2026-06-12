---
title: "Need help getting new remote up and running with lirc"
date: 2008-10-23
forum: General Help
---

### Post by beattyml1 on 2008-10-23
I've been using ubuntu for a few months now and I just got a remote that I was told works with LIRC, I installed lirc and lirc-x packages in synaptic without a hitch a window pop up asking about which remote I was using and I did not see mine on there so I selected the none option.  and clicked next hoping there was some sort of manual config, but there wasn't and now I can't figure out how to access LIRC to set it up or any thing regarding the x events that it supposedly uses. I am fairly new at this (not very good with the terminal) but willing to get my hands dirty if someone will guide me through it

---

### Post by Sin@Sin-Sacrifice on 2008-10-23
I got this from [http://shahrear.wordpress.com/]("http://shahrear.wordpress.com/")

Hope it's helpful. If you need help with the lircrc file then let me know. I've been spending a lot of time on this lately and found out a lot... I just don't know what you need to know other than what's below.



&#2437;&#2455;&#2494;&#2487;&#2509;&#2463; 5, 2006
more tips on using LIRC
&#2479;&#2494;&#2480; &#2437;&#2471;&#2496;&#2472;&#2503; &#2438;&#2459;&#2503;: Linux — pipasharto @ 11:08 am
Applications and LIRC Support

There are three kinds of applications:

   1. Those which could and actually have been built with LIRC support. These act as LIRC clients when there is a running LIRC daemon.
   2. Those which do support LIRC, but have not been compiled with the LIRC support enabled.
   3. Those which do not support LIRC at all.

Generally, most multimedia applications, video and audio players, TV viewers and FM tuner applications, support LIRC. Also, many applications provide a method (separate utility or options) to send commands to a running instance of the application. This is particularly useful for programs that belong to the 2nd and 3rd categories. LIRC provides an utility, called irexec (LIRC client), which can be used to execute any command we want. This way, those applications can be controlled with the remote control through LIRC.

In order to use our remote control with a certain application, we have to create a configuration file that contains the mappings between the remote control’s buttons and the commands that will be executed when each button is pressed.

This file can be:

    * named .lircrc and placed in the user’s home directory.
    * named lircrc (without the period in front of the name) and placed in the /etc/ directory for system-wide configuration.

Information about this file’s format can be found in the relevant section of the LIRC Documentation.
Quick Tests

Here are some sample .lircrc files, so that you can test your installation. Make sure you have loaded the proper LIRC module and you have started the LIRC daemon. Save one of them as .lircrc and place it in your home directory.

Special Note: In the following sample config files, substitute the remote control name with the name you have used for your own remote control and the button name with a name of any of your own remote control’s buttons.

The first two samples will work with Xine and MPlayer respectively. These two players are usually built with LIRC support and, when launched, they act as LIRC clients.

Load Xine and press the specified button on your remote control. It should toggle between full-screen and window-mode.

# .lircrc - XINE sample test
begin
    prog = xine
    remote = KWTV878RF
    button = ZOOM
    config = ToggleFullscreen
    repeat = 0
end

Use the following config with MPlayer.

# .lircrc - MPLAYER sample test
begin
    prog = mplayer
    remote = KWTV878RF
    button = ZOOM
    config = vo_fullscreen
    repeat = 0
end

For applications that are not LIRC clients themselves, but which provide a method to send commands to a running instance of the application, the configuration is a bit different. The LIRC client irexec is used in these cases. When you press a button on the remote control, irexec executes the specified command. This requires that irexec is running. Start it as a user:

# irexec

Save the following as .lircrc and launch TVtime. The specified button on the remote control should toggle between full-screen and window-mode.

# .lircrc - TVtime sample test
begin
    prog = irexec
    remote = KWTV878RF
    button = ZOOM
    config = tvtime-command TOGGLE_FULLSCREEN
    repeat = 0
end

To start irexec and have it run in the background, start it as shown below:

# irexec &

To kill it:

# killall irexec

Some hints for more complicated configurations

Here are some hints for those of you who need complicated setups.
Toggle Buttons

You can create toggle buttons, for example you can set the same button to Play or Pause a video stream, by setting two config = command directives. They will be executed in turns. For example:

# Toggle button example
begin
    prog = irexec
    remote = remoteA
    button = buttonA
    config = play_command
    config = pause_command
    repeat = 0
end

Using this configuration, when buttonA is pressed for the first time, the play_command is executed. The second time buttonA is pressed, the pause_command is executed.
Modes

Let’s assume that you want to control many applications with your remote control. Some of them are LIRC clients and some are controlled through irexec. You can define various modes (groups of button to command mappings), one for each application.

First of all, read the .lircrc format page from the LIRC Documentation very carefully.

Keep in mind the following rule:

    Each time you start a LIRC client and there is a mode within your configuration with a name equal to the application’s name, then this mode is automatically entered.

This means that if there is a mode named mplayer inside .lircrc and you start the mplayer program, which is a LIRC client, then the mplayer mode is automatically entered and only the button mappings that exist within this mode are functional.

Save the following as ~/.lircrc, substitute the remote control name and button names with your own, and start irexec:

# Example with modes

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

begin irexec

begin
        prog   = irexec
        remote = KWTV878RF
        button = 1
        # Start TVtime
        config = tvtime --window &
        # Enter tvtime mode
        mode = tvtime
    end

begin
        prog   = irexec
        remote = KWTV878RF
        button = 2
        # Start Totem player and play DVD
        config = totem dvd:/ &
        # Enter totem mode
        mode = totem
    end

begin
        prog   = irexec
        remote = KWTV878RF
        button = 3
        # Start Xine and play DVD
        config = xine dvd:/ --hide-gui &
        # Enter xine mode
        mode = xine
    end

end irexec

# ---------------
# MAIN END (irexec mode end)

# APP MODES BEGIN
# ---------------

# tvtime mode
begin tvtime
    begin
        prog = irexec
        button = POWER
        config = tvtime-command QUIT
        # Enter irexec mode
        mode = irexec
    end
    begin
        prog = irexec
        button = ZOOM
        config = tvtime-command TOGGLE_FULLSCREEN
    end
end tvtime

# totem mode
begin totem
    begin
        prog = irexec
        button = POWER
        config = totem --quit
        # Enter irexec mode
        mode = irexec
    end
    begin
        prog = irexec
        button = ZOOM
        config = totem --fullscreen
    end
end totem

# xine mode
begin xine
    begin
        prog = xine
        button = POWER
        config = Quit
        # Enter irexec mode
        mode = irexec
    end
    begin
        prog = xine
        button = ZOOM
        config = ToggleFullscreen
    end
end xine

# ---------------
# APP MODES END

I hope this example is clear enough. What is going on here is that when irexec (LIRC client) is executed, then the irexec mode is entered. When you press button “1&#8243;, then TVtime is launched and the tvtime mode is entered. When you press the “POWER” button, TVtime quits and the irexec mode is entered etc. etc.

Furthermore, even if you do not start irexec, when you launch any LIRC enabled application, like Xine, MPlayer, Gnomeradio etc, then the appropriate mode will be entered automatically and you will be able to control this application remotely.

As you have probably already read in the LIRC Documentation, you can modularize this configuration by keeping each application mode in a separate file. Just don’t forget to include those separate files by adding a line like the following in ~/.lircrc. For example:

include ~/.lirc/tvtime.lircrc

Final Notes

Maybe you will need some time to familiarize yourself with the .lircrc format and probably more time reading the LIRC documentation, but you will be satisfied with the result.

For information about what commands are available for each application, please refer to the application’s documentation, project web site or support forum.

Also, if you need more information or support for LIRC, please ask your questions in relevant web forums. I have written all I know in this guide, so I am afraid I cannot help you more.

LIRC can do more things, for example it can be used to transmit IR signals or to connect to other LIRC servers accross the network. These have not been covered, not only because I consider such info as “too much” for a new user, but also because I have not been able to devote any time to experiment with these features.

This guide was written while using a Fedora 4 system.
Further Reading

You should read:

   1. The LIRC Manual (Documentation)

&#2478;&#2472;&#2509;&#2468;&#2476;&#2509;&#2479; (&#2535;)

---

### Post by beattyml1 on 2008-10-24
does any one have a config file for this remote that they could send my way: 

Anyware GP-IR01BK Windows Vista Infrared MCE Black Remote Control

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003)

also do I need some sort of drivers or is lirc enough

---

### Post by beattyml1 on 2008-10-25
I'm hoping that maybe I could get some step by step total n00b directions on how to get this remote set up with the only starting assumptions being that I have installed thye lirc and lirc-x packages in synaptic, I would need to know the following things

is there a way to do this with out kernal recompilation

do I need to install seperate drivers for my remote and if so how would i get them and how would i install them

do i need to make a config file and if so and someone has one made for the above remote I would greatly appreciate if they would post it

I have tried to read the documentation provided by lirc.org but they lost me when they started talking about compling and scared me when they started talking about recompiling the kernal

---

### Post by beattyml1 on 2009-01-10
So I've finally started to get the basics of getting this set up, none of how it work really made sense until I started learning how terminal commands worked, but I still have some issues and was wondering if anyone could help with these

I'm having trouble setting up the following programs to work with lirc:
VLC
Rhythmbox
Elisa

This is what I have done:
Got the irexec to open programs
Got Totem commands to work

If anyone has a .lircrc file that works with these programs and would be willing to post that I think that would take care of my problem

---

