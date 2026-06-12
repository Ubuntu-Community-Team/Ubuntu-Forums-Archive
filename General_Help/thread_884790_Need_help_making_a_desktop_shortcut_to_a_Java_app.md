---
title: "Need help making a desktop shortcut to a Java app"
date: 2008-08-09
forum: General Help
---

### Post by ThrowThermalPod on 2008-08-09
HI,

I just installed the Axis and Allies clone Triple A (Which is absolutely amazing if you've never played it - [http://triplea.sourceforge.net/mywiki](http://triplea.sourceforge.net/mywiki)).

The problem is that it's a little awkward to launch for a newb Linux user like myself.  I was trying to make a shortcut that I could put on my desktop that would let me launch it. 

If I open the game's .sh file in a text editor, it reads:


```
if ! java -version > /dev/null 2>&1
then
echo "Could not find Java."
echo "You must have Java installed and in your path."
exit
fi

relativePathToGame=`dirname $0`
cd $relativePathToGame


java -Xmx196m -cp bin/patch.jar:bin/triplea.jar games.strategy.engine.framework.GameRunner

```

So my question is, if I right click on the .sh file in the game's directory and click Make Link, and then copy that Link to my desktop, could I just change the section:


```
relativePathToGame=`dirname $0`
cd $relativePathToGame
```

If I change this section to the actual file path, could that work?  I've tried a couple of different things, but it keeps changing the original file in the game's directory.

---

### Post by dexter on 2008-08-09
You could try making a symbolic link on your desktop pointing to the file you want to execute. This can be compared with a shortcut in windows.
To do this open a terminal, go to the desktop and create the link:
```

cd Desktop
ln -s JavaAppName /path/to/the/exectuble

```

You'll have to replace JavaAppName and /path/to/the/exectuble with the name and file you want.

---

