---
title: "HowTo: stjerm"
date: 2008-08-22
forum: General Help
---

### Post by billybag on 2008-08-22
stjerm is a really nice  and small quake-like terminal that runs very nicely with compiz. You can get the deb at getdeb.net [http://www.getdeb.net/app/stjerm]("http://www.getdeb.net/app/stjerm")

I personally prefer it over Tilda and Kuake. If you are looking for something similar to Tilda and the such and have found them a bit buggy, then i suggest this.

This is a really quick HowTo/Tip for getting started.

After you have installed the .deb...
First, you will need to create blank document in your home folder and name it .Xdefaults. Open this document and add the following:

This will set up the key(s) used to open the terminal:
```
stjerm.key: f8
``` You can change F8 to any other F key if you would like. If you would like it to be a combination of keys then use:
```
stjerm.keymod: shift+control
``` I am using shift and control as an example. Replace them with whatever you wish. If you would like to use the super(compiz)/windows button. Use 'windows' as the value without quotes.

Now lets give it some opacity (assuming youre using compiz). Default is 100
```
stjerm.opacity: 50
```

Next, lets give it a thin border. The default is no border, but i think it looks better with one
```
stjerm.border: thin
```
I also like to make the width a bit smaller. The default is 800. i like it at 600
```
stjerm.width: 600
```

I also prefer to have autohide turned off. It is turned on by default
```
stjerm.autohide: false
```

All in all, my whole .Xdefaults file looks like this:
```
stjerm.key: f8
stjerm.opacity: 50
stjerm.border: thin
stjerm.width: 600
stjerm.autohide: false
```
Save the file

Okay now that we have it set up to at least be launched when you hit the right key(s), lets create a menu item:

This part is easy, just type ```
stjerm
``` as the command and name it whatever you want and gives it whatever you want for a comment. I named it stjerm and for the comment, i just wrote "Quake-like terminal". Now when you click on your new menu item and hit your new execution keys, it should pop up from the top. To clearify, stjerm needs to be running in the background for it to work. that is the reason for the menu launcher. Once it is running in the background, you can then use the shortcut key(s) you created to open and close it

If you dont want to have to choose stjerm from your menu every time you want to start using it, then i suggest having it startup with your gnome session.

Having it startup with gnome is just as easy. Just click on "sessions" in your menu and then click ADD. Now put in the same info as you did with the menu item.

You may want to turn off certain compiz effects if you dont like how the terminal appears.

Now that you have the basic idea as to how to set up options, here are all the options and the tags to change them (taken by typing ```
stjerm --info
``` in terminal:
```


format: stjerm.OPTION: VALUE

OPTION   .Xdefaults options:    VALUE
  key:  	KEY      	Shortcut key (eg: f12).
  mod:  	MODIFIER      	meta modifier key: shift, control, alt, windows, none.
  keymod:  	MODIFIER      	Modifier for keyboard shortcuts. Can be a combination (with +) of modifiers (eg: shift+control).
  autohide:  	BOOLEAN      	Whether or not to hide stjerm when it looses focus. Default: true.
  font:  	FONT      	Terminal font and size (eg: Sans 10). Default: Bistream Vera Sans 10.
  background:  	COLOR      	Background color. Default: Black.
  foreground:  	COLOR      	Foreground color. Default: White.
  allowbold:  	BOOLEAN      	Allow bold fonts or not. Default: true.
  border:  	TYPE      	Border type: thin, thick, none. Default: none.
  opacity:  	NUMBER      	Opacity (range: 10 - 100). Default: 100.
  bgimage:  	FILE      	Background image to use on terminal.
  width:  	NUMBER      	Window width. Default: 800.
  height:  	NUMBER      	Window height. Default: 400.
  position:  	POSITION      	Window position: top, bottom, left, right. Default: top.
  scrollbar:  	POSITION      	Scrollbar position: left, right, none. Default: none.
  shell:  	STRING      	Terminal Shell. Default: the user's default shell.
  lines:  	NUMBER      	Scrollback lines. 0 to disable scrollback. Default: 1000.
  showtab:  	VALUE      	Tabbar visibility (one: only visible when > 1 tabs): never, one, always.
  tabpos:  	POSITION      	Tabbar position: top, bottom, left, right. Default: bottom.
  tablabel:  	STRING      	Label of the tabs. Default: term.
  tabfill:  	BOOLEAN      	Whether tabs fill whole tabbar space. Default: true.
  scroll:  	BOOLEAN      	Whether to scroll the terminal on output. Default: true.
  colorX:  	COLOR      	Specify color X of the terminals color palette
				You may specify no palette, or a complete one with 16 total colors.
				For this you have to use color0, color1, ..., color15.

```


COMPIZ:

If you would like to change the effect used when appearing and reappearing on your screen, open up your compiz settings manager. If you dont have 'animations' enabled, enable it. Open it and under the first tab, 'close animation' Click NEW Choose your animation and under window match, add the following ```
(class=Stjerm) & title=stjerm
``` The same goes for the 'open animation' tab

---

### Post by Diabolis on 2008-08-23
Got screen shots? It sounds a lot like [Tilda]("http://tilda.sourceforge.net/wiki/index.php/Main_Page").

---

### Post by Kadu on 2008-08-23
Well, it does sound like tilda. but let me tell you.

I have used tilda for quite a while and I also have tried guake. they both have many bugs and end up getting very annoying.

I've been using stjerm for a couple of months now and am much happier with it than i was with tilda.

if you like drop down terminals this is definitely the best one you can get. give it a go and you'll see.

---

### Post by billybag on 2008-08-23
it is like tilda (a quake-like terminal). But, as mentioned above, i too have had problems with Tilda and Kuake. Mostly compiz related. I have had no problems at all with stjerm and it is very light

[Homepage]("https://gna.org/projects/stjerm/")
[screenshot]("http://home.gna.org/stjerm/")

The screenshots in the picture, i feel, don't due it must justice. Remember that it is really customizable and so you can get it to look and act just like tilda except for sliding in and out. That i cannot seem to work out. I wish compiz had it for an animation option. That is the only drawback for me. i really like the sliding up and down effect of tilda. Instead i have mine set to the burn effect. It looks really cool that way

Kadu: Do you have your dropping down and sliding up? Do you have compiz? i would liek to know how you have it doing so.

---

### Post by Esthellin on 2009-09-11
This is the only thread that already had stjerm in it, so might as well relive an old thread.

I am using stjerm at the moment, and it is AWESOME. However, I have looked online and apparantly there are upgraded versions ([http://code.google.com/p/stjerm-terminal-emulator/](http://code.google.com/p/stjerm-terminal-emulator/)) that don't appear in the repositories when upgrading in synaptic. Is this because the link is for a stjerm for Fedora specifically and not others?

---

### Post by billybag on 2009-09-12
That is a good question. I do not see why it would not work with ubuntu. Perhaps it is just not that popular and so the ubuntu repos don't reflect the updates. Try looking for a repo that is privately maintained

---

### Post by kristopherw on 2010-09-07
Hello, I'm one of two active developers for stjerm. The site at Google code (stjerm-terminal-emulator) is a fork someone created, then apparently ditched. 

The active project by the original developers is at [http://stjerm-terminal.googlecode.com](http://stjerm-terminal.googlecode.com) 

I'm not exactly sure how to inform the Ubuntu package maintainers of the new home of the project so that newer versions make it into the repositories. 

The current version is still pulling from our old site at gna.org.

---

### Post by netimen on 2011-02-25
How do I make Ctrl-C work to stop the current task instead of copying the text to the buffer?

---

### Post by netimen on 2011-02-25
Rolled back to stjerm 0.11 and all works now perfectly for me!

---

