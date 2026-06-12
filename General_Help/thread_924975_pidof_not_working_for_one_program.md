---
title: "pidof not working for one program"
date: 2008-09-20
forum: General Help
---

### Post by momist on 2008-09-20
Hi, Can anyone explain why pidof works OK for some programs and not others?  I run a script using pidof to kill or start my Octoshape client, and this used to work OK.  Now though, the script is broken, and in a terminal pidof does not return anything when the program is running.

Here's the script:

[PHP]if pidof OctoshapeClient
then
 pkill OctoshapeClient
else
 exec ~/octoshape/OctoshapeClient -url:PARADISE.stream1_mp3 -nocache
fi[/PHP]

(I happen to really like that channel :) ) and terminal outputs:


[PHP] 
xxxxxx:~$ ps -e
<snip>
8310 ?        00:00:00 sleep
10331 ?        00:00:00 OctoshapeClient
10349 ?        00:00:14 OctoshapeClient
10367 ?        00:00:12 mplayer
11172 ?        00:00:23 firefox
11409 ?        00:00:00 sh <defunct>
11413 pts/0    00:00:00 ps
xxxxxx:~$ pidof mplayer
10367
xxxxxx:~$ pidof OctoshapeClient
xxxxxx:~$ 
[/PHP]

I don't know what has changed.

Ian

---

