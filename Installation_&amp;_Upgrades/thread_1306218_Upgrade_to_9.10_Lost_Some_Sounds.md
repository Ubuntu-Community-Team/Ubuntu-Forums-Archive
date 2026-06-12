---
title: "Upgrade to 9.10 Lost Some Sounds"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by nirvana21 on 2009-10-30
Last night I upgraded to 9.10. This morning I woke up and played some music from my disk without trouble. If I open firefox and try to play some music through flash player off the Internet, I get no sound. I thought maybe something was muted so I checked everything and its not that. I am not that educated in the ways of Ubuntu. I tried un-installing firefox, then reinstalling it along with flash player and the java plugin. That didn't help me. In fact now I can't get java to work which is really really bad!

So any ideas on how to fix my sound? Thanks in advance!

---

### Post by Iridias on 2009-11-01
I solved this Problem the following way:
[LIST=1]
[*] open the Package-manager of your choice.
[*] search for "pulseaudio"
[*] click on "delete" (and confirm delete also for the depending packages)
[*] go to a console
[*] type "sudo /etc/init.d/pulseaudio stop"
[*] restart firefox
[/LIST]

Thats what I've done - and now the sound is working again in flash.

---

