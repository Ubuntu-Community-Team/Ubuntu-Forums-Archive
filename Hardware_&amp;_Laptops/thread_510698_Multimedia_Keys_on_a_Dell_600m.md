---
title: "Multimedia Keys on a Dell 600m"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by DarkOx on 2007-07-26
Personally, I've been very happy with my Dell 600m computer, which seems to only get better as time goes on -- except the multimedia keys on it don't work out of the box on all distros. I got a PM asking me to explain how I got mine working, so here's a walkthrough on how to do it.

1st option -- upgrade to Fiesty. If I recall correctly (as I now use PCLinuxOS), Fiesty detected and enabled my multimedia keys out of the box. So this is probably your easiest bet.

2nd option -- use Keytouch. If, for whatever reason, you're not using Fiesty, this is the program you want to use. This is the method I'll be explaining.

First, download and install keytouch. You can probably find it in your distributions' repositories (it's in Ubuntus'), but you may want to download and install the latest version from [here]("http://keytouch.sourceforge.net/download.php").

Launch keytouch-editor. It will ask for your password; give it. It will then ask you to select a keyboard. I chose the default option: Device "event 0", Device name "AT translated set 2 keyboard", Bus "PS/2". It will ask that you hit an extra function key. Hit either of your volume keys or the mute key.

In the screen that follows, type in the name of your manufacturer, Dell, and model, 600m, in the boxes provided. Then, under the box that says "Keys", hit new, and press the desired button. Select the key, which should have the correct name, scancode and keycode assigned to it automatically.

Now change the default to program, and input a command that will have the desired effect. If you're using Kubuntu, it's probably best to control volume through Kmix, so use the following commands for your buttons:
                   Volume Up = dcop kmix Mixer0 increaseVolume 2
                   Volume Down = dcop kmix Mixer0 decreaseVolume 2
                   Mute = dcop kmix Mixer0 toggleMasterMute
You may have to play with these commands a bit to get them to work on your system. If you're using Ubuntu, you will have to find another command line program for your buttons. I used "aumix -w +3" for Volume Up and "aumix -w -3" for Volume Down in the past (never did find out how to get that mute button working without kmix, but it's probably possible). Save your configuration.

Now open Keytouch. Select the Keyboard tab, and select the file you just saved. The default settings should be fine. Now click apply. Your volume and mute keys should function correctly; though there won't be any visual cues when you press them.

---

