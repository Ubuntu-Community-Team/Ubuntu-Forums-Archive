---
title: "Firefox3 and Java - A tale told in screenshots."
date: 2008-10-17
forum: General Help
---

### Post by detroit/zero on 2008-10-17
I'll be right up front - I think FF3 sucks, at least the Linux version, anyways. The add-on development is going slow for FF3 extensions across all platforms (*"This add-on is for an older version of Firefox"*), and the available themes for FF3 Linux is sorrily lacking.

That being said - I still use it. It does work, and I think it's better than FF2 in some ways. I mean - whatever. I have a theme that blends well with my chosen desktop schemes, and Firefox keeps all my bookmarks in order. There's not much else to need beyond that. Except...

Java. Java has been a ***Royal*** pain across three versions of Ubuntu and two versions of Firefox. This current problem has been ongoing since Hardy's release and FF3's debut. When any site that uses Java opens in a Firefox window, my processor maxes out. It even goes past maxxed out - **102%**!! This is a horrendous problem, considering my addiction to Yahoo Pool.
[[IMG]http://img338.imageshack.us/img338/4271/ubuff3br1.th.png[/IMG]]("http://img338.imageshack.us/my.php?image=ubuff3br1.png")
Notice in Conky that FF is eating 102% of processing power, and the core temps are at 82 degrees Celsius and rising. This is after less than five minutes of playing Pool. 

So firstly, Ubuntu coming default with the largely useless IcedTea plugin was the first kick in the face. Having to hunt that down and remove it (along with - *Surprise!* - [Ubuntu Restricted Extras]("http://ubuntuforums.org/showthread.php?t=784384")), then do a trial and error tryout session with Java versions 1.5 and 1.6 to see which one (if any) will even work at all were kicks two, three, and four.

Kick five comes in when Java seems to work half-assed when it does actually work. Sometimes I have to close out Firefox two or three times to get Yahoo Games to even load game rooms. Even after the second, third - sometimes fourth - try, the secondary windows that open from inside (to check player profiles/scores and boot/invite windows) open up but they are blank gray boxes. Some java sites actually crash the browser and freeze my system, requiring a ctrl-alt-sysreq-k to restart. (see: [Zombie Infection Simulation]("http://zombies.kalleboo.com/"))

Just to make sure it was something worth complaining about, I opened up XP inside a VirtualBox VM. I installed Java (a less-than-three-minute, painless process) and POW! Just like that - playing Yahoo Pool with no multiple login attempts, problems, kinks, bugs, errors, or blank windows. Java running inside Firefox3, inside Windows, inside VirtualBox, **inside** Ubuntu works better, faster, and smoother than on my native platform. Check out this screenshot.. Low CPU temps, relatively low CPU usage, low memory usage... It's like heaven!
[[IMG]http://img338.imageshack.us/img338/6441/windowsvmna4.th.png[/IMG]]("http://img338.imageshack.us/my.php?image=windowsvmna4.png")
The thing is that as soon as I kill FF3 in Ubuntu, everything dies down and goes back to normal with 5 or 10 seconds of killing the process. (I say killing the process because Java always locks up Firefox so it has to be killed in the terminal.) If I forget to kill it (happened only once), My core temps will reach critical levels and the computer will do its' emergency shutdown thing.
[[IMG]http://img338.imageshack.us/img338/3825/afterjx4.th.png[/IMG]]("http://img338.imageshack.us/my.php?image=afterjx4.png")
So what's the problem? Does anybody have any guesses? 

I'm caught up on my updates, I've un/re-installed two versions of Java and the Mozilla Plugin from Synaptic, Add/Remove, and from scratch.

Can anybody tell me why Java and Firefox 3 are conspiring to kill my laptop? I'll happily provide any info that'll help.

---

### Post by detroit/zero on 2008-10-18
Bump.

---

### Post by detroit/zero on 2008-10-18
Wow! Posts sure do get buried fast here in the General Help forum.

At any rate, my long-sought Java-using experience has come to an abrupt and equally mystifying end.

After a good nights' sleep, when Loading XP in a VM to get some more Yahoo Pool action, as soon as the Java applet was loaded by FF, VirtualBox's CPU usage skyrocketed. Memory usage of course did not exceed the parameters set for the virtual machine (330MB RAM), but everything became slow and sluggish, and I was forced to kill the VM. I tried it a couple times to make sure I wasn't imagining things, but here's a screenshot of conky to tell the tale:
[[IMG]http://img262.imageshack.us/img262/313/newxpshotwp7.th.png[/IMG]](http://img262.imageshack.us/my.php?image=newxpshotwp7.png)
So the problem is somewhere between FF3 and Java - Ubuntu isn't the culprit.

What could have possibly changed inside a non-running Virtual Machine between last night when I made my initial post and today when I loaded it up again?

---

### Post by Dougie187 on 2008-10-18
Just so you know, you are not supposed to bump a thread within 24 hours, actually it hurts you more than anything, because there is a team of people specifically dedicated to solving threads that have not been answered in one day (but they have to have no replies which your's now does). 

On another note, I am not sure if this will help or not, but you should try checking your logs when that happens. I myself don't have any issues with java, though I will agree FF3 seems quite a bit more buggy than FF2. I end up having it freeze about once a day, and it is rather irritating. Either way, if you find something in the logs post it and someone will probably be able to help then.

---

### Post by toxent on 2008-10-18
Glad to see someone else is having mozilla3 and java problems.

i am running ubuntu 8.04, mozilla 3 and i play pogo.com which uses the java. it seems like to me,  ever since mozilla sent out 3, it takes multiple reloads of the same screen and/or restarts of mozilla3 to get java to load up properly. (sometimes stuck on the load icon screen, sometimes just blank) and sometimes I just have to re-login to get it all working.

I would love to find out why, and get it tweaked right.  I tried reinstalling java but no avail. (if i knew more about terminal and coding i most likely would be doing more to help out)

thanks.

---

### Post by detroit/zero on 2008-10-18
> **toxent said:**
> **Glad to see someone else is having mozilla3 and java problems.**

i am running ubuntu 8.04, mozilla 3 and i play pogo.com which uses the java. it seems like to me,  ever since mozilla sent out 3, it takes multiple reloads of the same screen and/or restarts of mozilla3 to get java to load up properly. (sometimes stuck on the load icon screen, sometimes just blank) and sometimes I just have to re-login to get it all working.

I would love to find out why, and get it tweaked right.  I tried reinstalling java but no avail. (if i knew more about terminal and coding i most likely would be doing more to help out)

thanks.
Um.. yeah.. me too :lolflag:

Anyways.. I'm going to head over to Mozilla support forums, since I think my results are pretty conclusive that the problem isn't in Ubuntu per se, it's rather between Java and Firefox 3.

---

