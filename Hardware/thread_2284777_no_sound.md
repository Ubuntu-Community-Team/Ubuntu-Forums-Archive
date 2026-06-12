---
title: "no sound"
date: 2015-07-01
forum: Hardware
---

### Post by richy2 on 2015-07-01
hi, i'm not used to umbuntu, so i need some help with not having any sound using umbuntu. so if anyone can give me some help

---

### Post by mattharris4 on 2015-07-03
The most common issue is Alsamixer being muted -- especially with Lubuntu but it happens with other Buntus as well.  Here are instructions to rectify this:

Check alsamixer.  Here is a link to instructions to fix several different issues regarding sound but you need section two:  [http://www.unixmen.com/2012003-howto...lem-on-ubuntu/]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/") .

Here is the pertinent info:

PulseAudio controls underlying ALSA-level volume controls. To change the ALSA-level volume controls directly, you can do [[COLOR=#009900]_the following_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/#"):Open a terminal. (The quickest way is the **Ctrl-Alt-T** shortcut)Enter** &#8220;alsamixer&#8221;** and press the Enter key.
In this user interface, you can do the following:

[LIST=1]
[*]Select your correct sound card using **F6 and select F5** to see recording controls as well
[*]Move around with left and right arrow keys.
[*]Increase and decrease volume with up and down arrow keys.
[*]Mute/Unmute with the **&#8220;M&#8221;** key. An &#8220;MM&#8221; means muted, and &#8220;OO&#8221; means unmuted.
[*]Exit from alsamixer with the Esc key.
[/LIST]


You will need to follow steps 2-4 with Master, Headphon and Speaker.  If  they aren't muted ("MM" under the graph bars means that function is  muted) before attempting to change them, you have another issue  entirely. 				

Good luck and I hope this solves your problem.  If Alsamixer isn't the problem click the link, it has instructions for other possible issues.

---

