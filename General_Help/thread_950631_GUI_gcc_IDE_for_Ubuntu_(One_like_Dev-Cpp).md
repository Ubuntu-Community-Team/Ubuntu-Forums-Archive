---
title: "GUI gcc IDE for Ubuntu (One like Dev-Cpp)?"
date: 2008-10-17
forum: General Help
---

### Post by Panarchy on 2008-10-17
Hello

Started learning some programming recently using
Sams Teach Yourself C++ in One Hour a Day

And have been using Dev-Cpp on windows for it.

Seems to work pretty nicely.

But I thought that it'd probably be good to use linux instead of/as well as windows for my education to be a C++ programmer.

So my question is. what's the **best** gcc IDE (a GUI one) to use?

Please reply, as I really want to compile things with a GUI (not command line).

Thanks in advance,

Panarchy

PS: I don't want to use the windows version of Dev-Cpp using WINE. I'd rather use a linux specific one!

---

### Post by Steveway on 2008-10-17
DEV-CPP hasn't been updated since 2005! I would not advise using that.
A good, cross-platform and still developed IDE is Code::Blocks.

---

### Post by Panarchy on 2008-10-17
So CodeBlocks is better than Dev-Cpp?

Is CodeBlocks the best C++ IDE?

Please reply

Thanks in advance,

Panarchy

PS: Download CodeBlocks now...

---

### Post by Sycron on 2008-10-17
> Is CodeBlocks the best C++ IDE?
This question is like: *Is Ubuntu the best Operating System ?*

And it sounds harsh.

Personally I'm using Code::Blocks and I like it. I tried other GUI's and IDE's but none of them satisfied me.

To install it, open up a terminal and type:```
sudo apt-get install codeblocks
```

---

### Post by dcontard on 2008-10-17
There are also other alternatives, like: 

[LIST]
[*][Eclipse]("http://www.eclipse.org/") with the [CDT Plugin]("http://www.eclipse.org/cdt/")
```
sudo apt-get install eclipse eclipse-cdt
```
[*][Anjuta]("http://anjuta.sourceforge.net/")
```
sudo apt-get install anjuta anjuta-common
```
[*][KDevelop]("http://www.kdevelop.org/")
```
sudo apt-get install kdevelop kdevelop-data
```
[/LIST]

This is not an exhaustive list, it has only some of the tools that I've tried for C++ programing, so maybe there are more options out there that could suit you better.

Code::Blocks is a good IDE for C++ in Linux (and other platforms), but if it doesn't like you, you could try these (and other) options. 

Surely there is no "Universal Best C++ IDE", it's a subjective choice based upon the different priorities and tastes that you, me and every other person has ;)

---

### Post by Panarchy on 2008-10-17
Well, okay!

Thanks guys!

I'll try all the IDEs mentioned, and then post on this topic which I find 'the best'.

Panarchy

---

### Post by Calmatory on 2008-10-17
Well, why don't you take it simple and use good ol' nano + gcc/g++? Edit the files with nano and compile with gcc/g++. This way, you can edit your projects from remote computers just by logging in via ssh. :) Besides this is a "skill" which you want to master. Makes life a lot easier with linux.

You could also use Gedit + gcc/g++. Edit with Gedit and compile via command line. Nifty.

But if you want to stick with an IDE, KDevelop might be nice, though Code::Blocks is the ultimate king(At least it was with Windows...)! ;)

---

### Post by snova on 2008-10-17
Never ask anybody on these forums what the "best" of anything is. It's entirely subjective and everybody will tell you something different. Keeping that in mind, here is a short list of some that I know of:

[LIST]
    [*] Eclipse - made up entirely of plugins, so very flexible.
    [*] NetBeans
    [*] KDevelop - A KDE program, so you might end up downloading enormous KDE support libraries.
[/LIST]

There are probably dozens. Some are more specialized. All you can do is try one and see if you like it, then try another...

And you'd be happier in Programming Talk if you're going to ask about this kind of thing.

---

### Post by Panarchy on 2008-11-15
^Hmm... thanks. I think I'll use Eclipse for when I move on to Java!

> **Calmatory said:**
> Well, why don't you take it simple and use good ol' nano + gcc/g++? Edit the files with nano and compile with gcc/g++. This way, you can edit your projects from remote computers just by logging in via ssh. :) Besides this is a "skill" which you want to master. Makes life a lot easier with linux.

You could also use Gedit + gcc/g++. Edit with Gedit and compile via command line. Nifty.

But if you want to stick with an IDE, KDevelop might be nice, though Code::Blocks is the ultimate king(At least it was with Windows...)! ;)

Thanks. Ah, I'm new to programming so I need a debugger as well! (gdb or whatever).

I've ended up applying an ubuntu theme to WINE and using Dev-C++ in WINE.

(also heard good things about Codeblocks)

Panarchy

---

