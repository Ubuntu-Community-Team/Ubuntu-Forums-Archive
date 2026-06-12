---
title: "absolute to relative symbolic links"
date: 2008-07-15
forum: General Help
---

### Post by soxs on 2008-07-15
I am going to make an icon theme, thus I need to create relative symbolic links, but rightclick create link to only creates absolute symbolic links to the icons which need  to be present multiple times.
So I am asking how to create relative symbolic links and if I can convert absolute symbolic ones to relative ones.
This is "mucho importante" as I would have to redo about 300 links by hand -.-

---

### Post by Bachstelze on 2008-07-15
Use the command-line, Luke ;)

```
ln -sf myFile myLink
```

for example :

```
firas@nobue test % ls -l
total 0
-rw-r--r-- 1 firas firas 0 2008-07-15 13:53 foo
firas@nobue test % ln -sf foo bar
firas@nobue test % ls -l
total 0
lrwxrwxrwx 1 firas firas 3 2008-07-15 13:53 bar -> foo
-rw-r--r-- 1 firas firas 0 2008-07-15 13:53 foo

```

(ln -s is usually enough, but since you seem to already have symplinks, using ln -sf will replace the old symlink with the new one.)

---

### Post by soxs on 2008-07-15
> **HymnToLife said:**
> Use the command-line, Luke ;)

```
ln -sf myFile myLink
```

for example :

```
firas@nobue test % ls -l
total 0
-rw-r--r-- 1 firas firas 0 2008-07-15 13:53 foo
firas@nobue test % ln -sf foo bar
firas@nobue test % ls -l
total 0
lrwxrwxrwx 1 firas firas 3 2008-07-15 13:53 bar -> foo
-rw-r--r-- 1 firas firas 0 2008-07-15 13:53 foo

```

(ln -s is usually enough, but since you seem to already have symplinks, using ln -sf will replace the old symlink with the new one.)

Well, thank you anyways, I allready knew tha :P .. seems to me I'll have to do a little script... I just thought there would be some option to get it done easier

---

### Post by Bachstelze on 2008-07-15
Then I don't think I understand what you want to do... Could you please explain it in detail ?

---

### Post by soxs on 2008-07-15
What I was searching was something utopic^^ Is there an option to chekc wether a file is a symbolic link in bash? [except for using grep "\->"]

---

### Post by Nimo on 2009-02-22
Maybe [http://tamacom.com/pathconvert.html](http://tamacom.com/pathconvert.html) could be of interest when it comes to convert between relative and absolute links.


You could use bash and if to check whether it is a link or not:
```
if [ -L = "/tmp/filename" ]
then
  echo "is a link"
else
  echo "is not a link"
fi
```

See [http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html) for more examples.

---

### Post by heindsight on 2009-02-22
Some time ago, I wrote a script to correctly create a relative symbolic link when the target is specified as either an absolute path or a path relative to the directory from where the script is called.

After seeing this thread, I found my old script, dusted it off a bit and added an option to convert an absolute symlink to a relative symlink.

I'm attaching it here, hope someone might find it useful.

**IMPORTANT:**
I make **NO** guarantees whatsoever regarding the safety or usefulness of this script. Use it at your own risk.

EDIT:
I made a few changes to the script which should fix the bugs pointed out by anonguy9
EDIT AGAIN:
fixed bug pointed out by ataraxic

---

### Post by anonguy9 on 2009-03-18
I'm not an Ubuntu user, but I bumped into this thread and it's on a topic I've been playing with.


> **heindsight said:**
> Some time ago, I wrote a script to correctly create a relative symbolic link when the target is specified as either an absolute path or a path relative to the directory from where the script is called.

I checked out your script, and it doesn't seem to work the way I expect.

There's an issue with some filenames:

```

ls -al *jack*
lrwxrwxrwx 1 user user 72 Dec 28 08:10 ACDC [1975, T.N.T #03] - The jack.mp3 -> /_media/music/unsorted-tested/ACDC/ACDC [1975, T.N.T #03] - The jack.mp3
```

```

relative.sh -c "ACDC [1975, T.N.T #03] - The jack.mp3" /home/user/bin/relative.sh: line 124: [: too many arguments
ln: target `jack.mp3' is not a directory

```


Also, what I consider to be an everyday use doesn't work:

```

echo foo>foo
ln -s `pwd`/foo bar
relative.sh -c bar

```

(and it just hangs)


This works, but it doesn't give the symbolic link I'm expecting:

```

mkdir 1
echo foo>1/foo
ln -s `pwd`/1/foo bar
relative.sh -c bar

```

I see bar -> ..//1/foo

I'm expecting bar -> 1/foo


I'm not up to speed enough with bash to hack your script, so I thought I'd ask.  I know that the last thing you want is to endlessly support a script, but I figured these were everyday issues and maybe I could nudge you into some help.  Maybe these issues are trivial for you.  =)

---

### Post by heindsight on 2009-03-24
Thanks for pointing out those issues. I'm uploading a new version which seems to work a lot better.

> **anonguy9 said:**
> 

There's an issue with some filenames:

```

ls -al *jack*
lrwxrwxrwx 1 user user 72 Dec 28 08:10 ACDC [1975, T.N.T #03] - The jack.mp3 -> /_media/music/unsorted-tested/ACDC/ACDC [1975, T.N.T #03] - The jack.mp3
```

```

relative.sh -c "ACDC [1975, T.N.T #03] - The jack.mp3" /home/user/bin/relative.sh: line 124: [: too many arguments
ln: target `jack.mp3' is not a directory

```

That was due to carelessness with quoting, leading to problems with filenames containing spaces...


> **anonguy9 said:**
> 
Also, what I consider to be an everyday use doesn't work:

```

echo foo>foo
ln -s `pwd`/foo bar
relative.sh -c bar

```

(and it just hangs)


This works, but it doesn't give the symbolic link I'm expecting:

```

mkdir 1
echo foo>1/foo
ln -s `pwd`/1/foo bar
relative.sh -c bar

```

I see bar -> ..//1/foo

I'm expecting bar -> 1/foo

Those were both due to a couple of bugs in the way I computed a common prefix of two absolute paths, in order to compute a relative path from the link to the target.

---

### Post by anonguy9 on 2009-03-25
Thank you for your effort.  I'm pleased you could respond so quickly and had time to pour over old code.

I tracked down one remaining issue, and I made some scripting to easily reproduce it.


This works as expected:

(downloaded relative.sh from [post #7](http://ubuntuforums.org/showpost.php?p=6782987&postcount=7))

```

SOURCE_NAME="source"
cd /tmp
mkdir relative.sh.$PPID
cd relative.sh.$PPID
touch "$SOURCE_NAME"
ln -s "$PWD/$SOURCE_NAME" link
ls -al ./link
# Assumes that relative.sh was downloaded to /tmp
chmod +x /tmp/relative.sh
/tmp/relative.sh -c link
ls -al ./link
cd /tmp
rm -rf /tmp/relative.sh.$PPID

```

lrwxrwxrwx 1 user user 33 Mar 25 12:14 link -> ../../tmp/relative.sh.3012/source

It's not as clean as  it could be, but it works.  I'm sure it can trivially be cleaned with some existing tools, and I could code something in Ruby if I cared.

Now let's try with another name:

SOURCE_NAME="ACDC [1975, T.N.T #03] - The jack.mp3"

The rest is the same.  I now get:

lrwxrwxrwx 1 user user 272 Mar 25 12:19 ./link -> ../../tmp/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3//tmp/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3/ACDC [1975, T.N.T #03] - The jack.mp3

All other use cases shown in [post 8](http://ubuntuforums.org/showpost.php?p=6920263&postcount=8) work as expected.


--------------------------------------------


New topic: PathConvert, for anyone and everyone.

As an aside, I did already check out PathConvert, but it looks terribly dated and I'm scared to go near it.

I did try to compile it, but perhaps my gcc version isn't what's expected or it's just so hopelessly dated that things are quirky with current tools.

I did track down the specific version of fileutils which was mentioned by PathConvert.

I don't particularly care about getting this working.. but it really surprises me that this kind of tool isn't already finished and stable in a dozen different projects.

My notes are below.  Help if you can, otherwise this is just for posterity.

= gnuln =

NOTE: Archives of fileutils can be found here: [http://www.filewatcher.com/m/fileutils-3.16.tar.gz.856021.0.0.html](http://www.filewatcher.com/m/fileutils-3.16.tar.gz.856021.0.0.html)

```

wget http://tamacom.com/pathconvert/pathconvert.tar.gz
tar xvf pathconvert.tar.gz
cd pathconvert/gnuln/
wget ftp://ftp.uni-hannover.de/pub/mirror/gnu/old-gnu/fileutils/fileutils-3.16.tar.gz
tar xvf fileutils-3.16.tar.gz
cp ../lib/abs2rel.c ../lib/rel2abs.c fileutils-3.16/lib
cp Makefile.in fileutils-3.16/lib
cp ln.c fileutils-3.16/src
cp ln.1 fileutils-3.16/man
cd fileutils-3.16
./configure
make

```

gives me:

```

make all-recursive
make[1]: Entering directory `/mnt/sda8/user/_public/live/working/pathconvert/gnuln/fileutils-3.16'
Making all in lib
make[2]: Entering directory `/mnt/sda8/user/_public/live/working/pathconvert/gnuln/fileutils-3.16/lib'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I. -I../intl  -g -O2 -c userspec.c
userspec.c:88: error: expected identifier or ‘(’ before ‘__extension__’
make[2]: *** [userspec.o] Error 1
make[2]: Leaving directory `/mnt/sda8/user/_public/live/working/pathconvert/gnuln/fileutils-3.16/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/mnt/sda8/user/_public/live/working/pathconvert/gnuln/fileutils-3.16'
make: *** [all-recursive-am] Error 2

```

---

### Post by heindsight on 2009-03-25
> **anonguy9 said:**
> Thank you for your effort.  I'm pleased you could respond so quickly and had time to pour over old code.


no problem - this is what i do for fun ;)

> **anonguy9 said:**
> 
Now let's try with another name:

SOURCE_NAME="ACDC [1975, T.N.T #03] - The jack.mp3"

The rest is the same.  I now get:

lrwxrwxrwx 1 user user 272 Mar 25 12:19 ./link -> ../../tmp/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3//tmp/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3/relative.sh.3012/ACDC [1975, T.N.T #03] - The jack.mp3/ACDC [1975, T.N.T #03] - The jack.mp3


Oh dear. I hadn't even thought of that! It's because of the **[1975, T.N.T #03]** in the filename.
The shell parameter expansions I used to build up the path try to match that whole sequence to a single character (one of the characters between the brackets) instead of to the literal string [FONT="Courier New"][1975, T.N.T #03][/FONT]

I expect something similar will happen with names containing * and ?
I'll have to go through all the parameter expansions and fix that...

EDIT:
OK, I think I've fixed that now, but with how this has been going there's probably still a horde of other bugs in there ;)

---

### Post by anonguy9 on 2009-03-26
Thanks again for the update.  Out of 677 links going all over my filesystem, only one link was broken by relative.sh.  I'll track that issue down soonish.

----

For others who may be following this thread or who may find it someday in the future..

Executing a command on a group of files which have spaces in their name (using bash):

```

find . -name '* *' | while read i; do relative.sh -c "$i" ; done

```

Or on a particular wildcard, like so:

```

find . -name 'File*' | while read i; do relative.sh -c "$i" ; done

```

I know I know.. it's totally obvious to anyone with a few decades of experience.

----

I also bumped into some kind of fundamental limitation to something or other.  It's not you, it's me.  Well, it's Linux.  I think it's mad at me.

There's no bug to fix, so this is just some fun reading.  I'll attempt to walk you through it.

```

su

cd /
mkdir -p /1/1/1/source_dir/
touch /1/1/1/source_dir/source_file
mkdir -p /1/1/0/linked_dir/
ln -s /1/1/0/linked_dir /0
ln -s /1/1/1/source_dir/source_file /0/source_file_linked
# This works:
ls -al /1/1/1/source_dir/source_file /0/source_file_linked

# Note: I'm making relative.sh pass through that linked directory.
# This is a rather interesting problem.
/tmp/relative.sh -c /0/source_file_linked

# This does not!
ls -al /0/source_file_linked
ls -al /1/1/0/linked_dir/source_file_linked

# Look at my original "ls":  ls -al /1/1/1/source_dir/source_file /0/source_file_linked
# You can see that "../" replaces "/0/" and ../1/1/1/source_dir/source_file looks sensible.
# but cd into /0 and try to ls ../ and what do you see?
# What you expect is to see your root filesystem.

cd /0
ls ../

# But what you actually see are the contents of /1/1/0 (linked_dir/)
# Why?  Dunno. (Linux secretly hates me.  Ok, maybe not so secretly.)

# Solution?

cd /1/1/0
ln -s /1

# Yep, that works.
ls -al /0/source_file_linked

# Clean up (be careful, you are root!)
rm -i /0
rm -ri /1

```

---

### Post by heindsight on 2009-03-26
> **anonguy9 said:**
> 
```

su

cd /
mkdir -p /1/1/1/source_dir/
touch /1/1/1/source_dir/source_file
mkdir -p /1/1/0/linked_dir/
ln -s /1/1/0/linked_dir /0
ln -s /1/1/1/source_dir/source_file /0/source_file_linked
# This works:
ls -al /1/1/1/source_dir/source_file /0/source_file_linked

# Note: I'm making relative.sh pass through that linked directory.
# This is a rather interesting problem.
/tmp/relative.sh -c /0/source_file_linked

# This does not!
ls -al /0/source_file_linked
ls -al /1/1/0/linked_dir/source_file_linked

# Look at my original "ls":  ls -al /1/1/1/source_dir/source_file /0/source_file_linked
# You can see that "../" replaces "/0/" and ../1/1/1/source_dir/source_file looks sensible.
# but cd into /0 and try to ls ../ and what do you see?
# What you expect is to see your root filesystem.

cd /0
ls ../

# But what you actually see are the contents of /1/1/0 (linked_dir/)
# Why?  Dunno. (Linux secretly hates me.  Ok, maybe not so secretly.)

```

hehehe, i can see how that can be surprising, but it actually makes perfect sense. The **..** entry in each directory is a hardlink to the parent directory. Your /0 is a symbolic link to /1/1/0/linked_dir and thus /0/.. is a hardlink (ie the same directory as) /1/1/0. Thus, the relative symlink /0/source_file_linked pointing to ../1/1/1/source_dir/source_file resolves to 0/../1/1/1/source_dir/source_file, which is /1/1/0/1/1/1/source_dir/source_file. 

You can observe a similar effect by doing:
```
mkdir -p foo/bar
ln -s foo/bar baz
touch baz/../quux
```
You'll notice the file foo/quux is created (not ./quux)

Also try doing:
```
stat baz
stat baz/.

```
And you'll notice that baz/. is not the same file as baz, because baz is a symbolic link to foo/bar and baz/. is a hardlink to foo/bar

---

### Post by anonguy9 on 2009-03-26
```

mkdir -p foo/bar
ln -s foo/bar/baz
touch baz/../quux

```

=>

```

mkdir -p foo/bar
ln -s foo/bar baz
touch baz/../quux

```

=)

-

> And you'll notice that baz/. is not the same file as baz, because baz is a symbolic link to foo/bar and baz/. is a hardlink to foo/bar

Whoa. o_O

-

I have to redo some scripting, and I'll be doing some testing with 10k+ different links.  I'll drop back in with the results.  =)

---

### Post by heindsight on 2009-03-26
> **anonguy9 said:**
> ```

mkdir -p foo/bar
ln -s foo/bar/baz
touch baz/../quux

```

=>

```

mkdir -p foo/bar
ln -s foo/bar baz
touch baz/../quux

```

=)


Well spotted. Don't know how that happened :oops:

---

### Post by ataraxic on 2009-04-20
Thanks for great [[COLOR="Blue"]script[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=107617&d=1238012714"), [**[COLOR="DarkRed"]heindsight[/COLOR]**]("http://ubuntuforums.org/member.php?u=222765"). That's exactly I've been searching for! I'm using it in my driver Kbuild Makefiles to convert abs dir pathes into relative one.
Corrected some minor bug in common_prefix() function, and adapt it a little for a specific cases to make it work. I call it abs2rel.sh. It will work at [[COLOR="Blue"]CERN[/COLOR]]("http://en.wikipedia.org/wiki/CERN") now (-;

---

### Post by heindsight on 2009-04-20
> **ataraxic said:**
> Thanks for great [[COLOR="Blue"]script[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=107617&d=1238012714"), [**[COLOR="DarkRed"]heindsight[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=860064"). That's exactly I've been searching for! I'm using it in my driver Kbuild Makefiles to convert abs dir pathes into relative one.
Corrected some minor bug in common_prefix() function, and adapt it a little for a specific cases to make it work. I call it abs2rel.sh. Will work at [[COLOR="Blue"]CERN[/COLOR]]("http://en.wikipedia.org/wiki/CERN") now (-;

Glad you found it useful :-)
I'd like hear a bit more detail on the "minor bug" you fixed in common_prefix()

---

### Post by ataraxic on 2009-04-20
> **heindsight said:**
> Glad you found it useful :-)
I'd like hear a bit more detail on the "minor bug" you fixed in common_prefix()

p1 && p2 should be initialized

```
p1="$1"
p2="$2"
```

Nevertheless, even without initialization - the whole script works anyway, but really in a nasty way.

If you'll just try to call common_prefix() function with or without parameter initializaion - you'll see the difference. Without init - it's always root dir ( / )

---

### Post by heindsight on 2009-04-20
> **ataraxic said:**
> p1 && p2 should be initialized

```
p1="$1"
p2="$2"
```

Nevertheless, even without initialization - the whole script works anyway, but really in a nasty way.

If you'll just try to call common_prefix() function with or without parameter initializaion - you'll see the difference. Without init - it's always root dir ( / )

Wow, thanks for that. I would call that more than just a minor bug though :)

---

### Post by ataraxic on 2009-04-20
> **heindsight said:**
> Wow, thanks for that. I would call that more than just a minor bug though :)

I think your script is really a good example to submit  to [**[COLOR="Blue"]Advanced Bash-Scripting Guide[/COLOR]**]("http://tldp.org/LDP/abs/html/") "List of Examples" chapter. It would be a shame not to share it.
Cheers.

---

### Post by anonguy9 on 2009-05-09
I think this script should be included with all Linux distributions.  =)


It's yet another example of GNU's "go do it yourself, we hate you" attitude.  With them, everything is possible, and yet all these "common" situations aren't handled because they're "possible" through other means.  Except normal humans can't code around the limitations that the oversimplified GNU software gives.

Oh, was I ranting?  =/

---

### Post by NutMonkey on 2009-07-22
Found this thread looking for a way to convert absolute symbolic links to relative links.  I wanted to mention there's also a package "symlinks" that will take care of it also.

symlinks -c -r .

will convert all the symbolic links in your current directory or subdirectories.

---

### Post by nikobonnieure on 2010-02-06
Thanks a lot for your script

i have been using it for converting a full tree of symlinks from absolute paths to relative paths.
I prefer to do them with the mouse in gnome, and then convert, it is quicker.

Anyway, there is a little bug in the script, please correct in the original file:
at the end of the file, before issuing the ln command you have:
if [ -d "$TARGET" ]; then
    TARGET="$TARGET/"
fi

if [ -d "$FRM" ]; then
   FRM="FRM/"
fi


first of all, the instruction FRM="FRM/" is not correct and is buggy if the destination of the link is a directory. the instruction should be FRM="$FRM/"

anyway, the whole 'if' block is unneeded and even, buggy also. due to the recursive algorythm at the end of make_relpath() function, a trailing / should not be added to the FRM. If it was added, then an extra level of ../ would appear in the target path.

So this block that adds a trailing / to FRM is buggy and unneeded.
Thanks to remove it and to make the end of the script file looks like:

if [ -d "$TARGET" ]; then
    TARGET="$TARGET/"
fi

TARGET=$(make_relpath "$TARGET" "$FRM")
echo "ln $LNOPTS \"$TARGET\" \"$FRM\""
# Create the link
ln $LNOPTS "$TARGET" "$FRM"

---

### Post by porg on 2010-08-03
@heindsight: Your script helped me very much! Thanks! porg


How **relative.sh** helped me:

I have a tutorial file collection, where the real files only exist at one place in the hierarchy, but aliases to them were created in various category directories (by means of the Mac OS X Finder) so that the same content could be browsed through different approaches.

This collection is natively viewable even within the dumbest file browser, without the need to support something sophisticated such as a tagging/filtering/sorting browser system.

Now I wanted to move this collection to a SD card for use with my cellphone's eReader.

1) I had to convert Mac OS X aliases to standard Unix symbolic links. I used the script [**alias2ln**]("http://www.macosxhints.com/article.php?story=20021024064107356").

2) **alias2ln** created absolute symlinks, which are of no use if my SD card is inserted at a different mount-point (or other home directory) such as within the cellphone! Hence I needed to convert the absolute into relative filepaths. Your script **relative.sh** did a wonderful job!

---

### Post by phorminx on 2010-10-02
@NutMonkey  	

symlinks can be quite helpful for converting existing links.
relative.sh can also be used as a replacement for "ln -s" that gives you relative links right away. Also, it's easier to customize a shell script than a binary (even with open source code).

@nikobonnieure

I agree with him that at the end of the script there is a bug. Yet I found that his approach of simply remove that if statement didn't work for me either. I use instead

if [ -d "$FRM" -a "x${FRM%/}" = "x$FRM" ]; then
    FRM="$FRM/"
fi

---

### Post by porg on 2010-11-07
**Bug 1**: relative.sh failed when applied on directories, as noted by @nikobonnieure. Thanks!

For those who didn't understand @nikobonnieure's sentence "Thanks to remove it and to make the end of the script file looks like" a short clarification here:

This script is a frontend to "ln. The "ln" argument "target_dir" must not have a trailing slash.
For me it worked to simply erase the whole block:

```

if [ -d "$FRM" ]; then
    FRM="FRM/"
fi

```

**Bug 2**: If your absolute symlinks have more than one consecutive space character in their filename, relative.sh creates false relative symlinks, as it normalizes all those whitespace to one-space-only.

The bug must be within the function make_relpath(). I was just nor able to track it down, as I am not really familiar with bash scripting.

Could someone please isolate the bug? Thanks!

---

### Post by snotplop on 2012-09-26
Let's drudge this thread up from the dead! I've been searching for an elegant way to do do this for the past three weeks, like so many of you now years ago.

Please have a look at the package 'symlinks' in the ubuntu repositories.

Using this package, this command will convert all absolute symlinks within '/path/to/symlinks' to relative links, AND clean them up in the process:
```
symlinks -c /path/to/symlinks
```Pretty neat little package. There's a whole host of other symlink-related magic tricks this will accomplish as well.

---

