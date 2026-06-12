---
title: "howto disable some features of touchpad ???"
date: 2009-07-07
forum: Hardware
---

### Post by mikesf on 2009-07-07
hi,
running ubuntu 9.04 on lenovo s10 netbook. the touchpad works perfectly fine ... however, i can't STAND how touching it in the Top Right Corner
1) pastes all kinds of crap into whatever document i'm working on
2) shuts down tabs from text editor or firefox

a few things BEFORE YOU ANSWER THIS POST

1) i don't want to disable the touchpad or clicks entirely ... I STILL NEED and would like the touch-to-click features as well as scrolling to work
2) i just want to disable or control certain features, e.g. disable "top-right-corner tap" having a special annoying feature.

also ... i'm pretty ticked at whoever made this feature and didn't provide an easy control to modify the zones of the touchpad.

---

### Post by teknodude on 2009-08-23
I'm gonna respond to bump this post, because I run into the same problem when typing anything. I think there is a fix for people running fedora core.

---

### Post by loomsen on 2009-08-23
Hello.

Do you have the pkg gsynaptics installed? It let's you configure your touchpad's default behavior. Working for me, tho I'm running fedora (but I'm pretty sure there's a similar package for debian systems too)

aptitude install gsynaptics

---

### Post by mikesf on 2009-08-25
i enabled both synclient and gsynaptics by enabling SMHConfig by creating the file /etc/hal/fdi/policy/shmconfig.fdi and adding the following

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>

according to this post:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

although both synclient and gsynaptics work, these utilities do not allow one to configure anything useful. in particular, they don't allow you to configure (turn off) the silly upper right hand corner tapping on the mouse pad. i am SOOOO dissapointed in that. here's why ...

1) when you apt-get install something, you expect it to work. NEITHER synclient or gsynaptic work from an install. they both need you to enable SHMConfig. 

2) enabling SHMConfig should just be a matter of editing xorg.conf HOWEVER, ubuntu doesn't seem to really use this anymore. AND where in the documentation do they tell us that? it's like ubuntu is getting dumber and dumber. every release becomes as stupid as microsux windows. how can you stop using major linux conventions, and then not make it plainly visible to the user???

3) after the months of dealing with this problem, with no help from any genius at ubuntu or canonical ... i finally read the tutorial on how to configure the touch pad and then .... the stupid synclient or gsynaptics has no features other than turn off taps, etc...

i think this is a pretty serious mistake. not being able to control the touch pad is such a nuisance that i really question why i'm using ubuntu anymore. yeah ... it was easy to install and wireless works, but this is hardly linux. no wonder all my gentoo and fedora friends laugh at me when i tell them i run ubuntu.

---

