---
title: "SCiM-pinyin input disappeared!!"
date: 2008-09-15
forum: General Help
---

### Post by nakyo on 2008-09-15
I used SCiM-pinyin (smart pinyin input) to type simplified Chinese but start from yesterday I realized it doesn't appear in my SCIM manu anymore.. I reinstalled SCIM-pinyin package, and from SCIM set up I can see Smart-pinyin is installed.. just don't know why it doesn't appear.

Here is the screen shot of the set up. From left side "IMEngine" you can see there is the option "Smart pinyin" but right side, it is not appearing in my "installed input method".

I can use all other input methods like WuBi, ErBi, Chewing...but the only one I need is pinyin..

I found similar posts but none of them really solves my problem:
[http://www.scim-im.org/forums/scim_user#nabble-td17186254](http://www.scim-im.org/forums/scim_user#nabble-td17186254)
[http://ubuntuforums.org/showthread.php?t=194513&page=3](http://ubuntuforums.org/showthread.php?t=194513&page=3)

btw, how can i remove all the scim files? I tried
> sudo rm -rf /etc/scim
sudo rm ~/.scim
sudo rm /root/.scim
but it doesn't work..
and I tried to completely uninstall all the scim files and reinstall them but still not working..](*,)

Thanks!

---

### Post by seshomaru samma on 2008-09-20
try it another way:
run 
> ps aux | grep scim
you will get an output with lots of lines like this:
> Sesho    ** 5102**  0.0  0.0      0     0 ?        Z    Sep19   0:00 [scim] <defunct
notice the numbers in bold, they are the process number 
kill them like this
> kill 5102
make sure you kill all the processes 
run ps aux | grep scim again just to make sure 
(if you killed all of scim process you should only get one line:
> Sesho    17358  0.0  0.0   2976   748 pts/0    R+   15:48   0:00 grep scim)


. .go to places>home
press ctrl+h to show hidden files
go to the .scim folder 
delete every file in there
reboot

---

### Post by nakyo on 2008-09-20
It worked!! Thanks a bunch seshomaru..
just for the ones who have the same problem:

after totally removed scim, go to system-> administration -> language support and install chinese and restart..

&#32456;&#20110;&#21487;&#20197;&#25171;&#20013;&#25991;&#20102;&#65281;&#65281;

---

### Post by chuang39 on 2010-06-25
Congrats, it helps.

---

