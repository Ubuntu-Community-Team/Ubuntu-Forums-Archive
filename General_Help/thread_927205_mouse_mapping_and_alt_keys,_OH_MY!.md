---
title: "mouse mapping and alt keys, OH MY!"
date: 2008-09-22
forum: General Help
---

### Post by bgugi on 2008-09-22
and so i turn again to a forum that seems to ignore me in all possible ways.

here's a double for ya.

i have a dell latitude d610, with both trackpoint and touchpad mice, each with two buttons.
back in my w[-Xws days, i used blender. i friggen loved blender. one of the major things for flying around blender was the mmb, which is in windows (and as far as i can tell, linux also) emulated with alt-lmb.


problem 1:apparently metacity holds onto alt-drag, can i disable this?

problem 2:i tried mouseemu([http://ubuntuforums.org/showthread.php?t=469125](http://ubuntuforums.org/showthread.php?t=469125)  didn't mess with xorg settings, just mouseemu), but it didn't feel right. after removing, i noticed my hotkeys for amarok stopped working (ctrl-alt-instert/home/pgup/pgdwn) when i use the right alt key. trying to map the right alt in amarok told me iso_level3_shift, which is apparently a keystroke (not a modifier). i reinstalled mouseemu, removed all the bindings from the config, restarted, and re-removed. still didn't work. the right alt works for switching to the (tty's?, ctrl-alt-f1,8), but not for pulling up the 'run application' or terminal (alt-f2,3)

---

### Post by bgugi on 2008-09-25
bump, and additional

fn key works in some combinations:

fn-(bluenumbers) used to work, but stopped no output at all(with numlock on or off; again, sucks with blender), 
fn-pgup/pgdwn/end works (volume control),
fn-numlock doesn't work (scroll lock, what is that anyways?), 
fn-up/down works(brightness), 
fn-esc works(standby), 
fn-f2 works (wifi toggle)
fn-f3 works (battery info)

messing around with "keyboard preferences" didn't seem to work

if you guys can't give me an answer, could you direct me to somewhere else that could? it seems this community isn't as helpful as i suspected it would be.

---

### Post by bgugi on 2008-09-27
weirdness.

i messed up my superblock on my linux partition last night, and was freaking out until i booted livecd and ran a fsck and kept hitting y

whether it was related or not, my right alt key works now. i also noticed that i turned on keyboard mouse control, which was holding my numpad hostage.

which leaves the only other question: is it possible to unbind the alt-drag to move windows in metacity?

---

