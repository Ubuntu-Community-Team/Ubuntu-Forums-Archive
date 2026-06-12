---
title: "looking for Intel HD 3000 driver + Nvidia GT 555M on lenovo Y570 but not working :("
date: 2012-01-16
forum: Hardware
---

### Post by amirhussein on 2012-01-16
Hi,

I've just installed linux ubuntu 10.10 on my lenovo Y570 (i7 2670, 8gb ram, Intel HD 3000 + Nvidia GT 555M 2gb) and **I don't want to upgrade to higher versions.** As I need to use a software which is just compatible with 10.10 (I tried it with 11.10 but not working :( )

For using graphical interfaces how can I install Intel HD 3000 graphics on it? I'm completely newbie to linux, completely! :D
After it, How can I use Nvidia optimus capability in linux? How can I install it?

---

### Post by Lekensteyn on 2012-01-21
Intel HD 3000 graphics should work out of the box (newer versions of Ubuntu with newer kernels have better support for such recent hardware). As for your Optimus question, there is [Bumblebee](http://askubuntu.com/a/36936/6969), but the Lenovo Y570 (and Y470 too) are currently not supported by the driver nor the power saving feature. Work is going on to make it work though. [https://lists.launchpad.net/bumblebee/msg00070.html](https://lists.launchpad.net/bumblebee/msg00070.html)

---

### Post by varunendra on 2012-01-22
> **amirhussein said:**
> ....and **I don't want to upgrade to higher versions.**
Just three days ago, I could write the same thing in even larger and bolder letters ;),
But after experiencing the instability of system with backported drivers on 10.04.3, and the out-of-box stability of 11.10 (with atheros wireless and Intel HD graphics + everything else), now I suggest it to everyone who has a sandy-bridge processor.

In case you want to stick with 10.10 anyway (let's hope it works better for you), this post by *realzippy* is what worked for me (until Alt+tab bug forced me to switch to 11.10 - for good!): [http://ubuntuforums.org/showpost.php?p=11293236&postcount=10](http://ubuntuforums.org/showpost.php?p=11293236&postcount=10)

The repository he has added to in his first command is supposed to have the most stable backported driver for Intel HD graphics: [https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=lucid](https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=lucid)


[B]_PS_:
[/B]By the way, would you like telling us the name and version of the software which you have to use on 10.10? Maybe porting it to 11.10 could be easier and more promising than using backported drivers on 10.10.

---

### Post by fabio.hipolito on 2012-05-14
Hi,

have you tried Bumblebee for nvidia support? See [bumblebee-project]("http://www.bumblebee-project.org/install.html#Ubuntu") and try to install it.

Lenovo's Y470 and Y570 are known for have a bug, to work it around see [Lekensteyn's solution]("https://github.com/Bumblebee-Project/bbswitch/tree/ec42e5b7ad3643a94fedf325cd7ec21a0ad5e712").

Cheers.

P.s.
I am running Ubuntu 12.04, I not sure if this will be compatible with 10.10

---

