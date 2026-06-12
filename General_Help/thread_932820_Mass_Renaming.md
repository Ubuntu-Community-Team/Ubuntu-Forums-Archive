---
title: "Mass Renaming"
date: 2008-09-28
forum: General Help
---

### Post by Literati on 2008-09-28
I want to rename ALL the folders in my /home/music to replace any . ' " [ ] ! @ with a space. HOWEVER, from what I've been reading, if I replace the ., it will also remove it from say, "blah.mp3" making the files useless when I switch to my Windoze boot.

If possible, I would only like to rename FOLDERS, hence killing the worry about blah.mp3

If it, at the same time, could Make Folders Start With A Captial On Each Word, that'd be great too :)

Thanks for your responses :)

---

### Post by taladan on 2008-09-28
You're likely going to have to script this as it's fairly specialized (though there might be a utility out there to do this).  A friend of mine wrote a script similar to what you're wanting to do and it's at:

[http://ftp.thomason.homeip.net/Scripts/rmp3.sh]("http://ftp.thomason.homeip.net/Scripts/rmp3.sh")

What it does though is translates any spaces in a filename into a "_" (underscore) in all directories and directory names below your current one.

Likely with some tweaking you could fix it to do what you need it to.

Hope this helps,

Tal

---

### Post by michaelzap on 2008-09-28
I think you should be able to do this with GPRename. Just change all occurences of .mp3 to *mp3 first, then change the other characters to spaces, and then replace *mp3 with .mp3. You might also be able to use a decent mp3 tagging tool like Ex Falso to do this (you can create tags from the file names if your files don't have tags, and then you can rename the files based on the tag names stripping out the funky characters).

---

### Post by unutbu on 2008-09-28
This script does mass renaming:
[list]
[*]It only renames directories, not files
[*]It changes .,'"[]!@ to spaces 
[/list]
Save the script in a file named rm_spaces.py

[php]#!/usr/bin/env python
import os
import optparse
usage = "usage: %prog [options]"
parser = optparse.OptionParser(usage=usage)
parser.add_option("-x", "--doit", dest="doit",
                  action="store_true", 
                  default=False,
                  help="really do it")

(opt, args) = parser.parse_args()   

argpath=args[0]
print "argpath=%s"%argpath

failures=[]
for root, dirs, files in os.walk(argpath,False):
    for name in dirs:
        dirname=os.path.join(root, name)
        new_name=name.title()
        for char in ['.',"'",'"','[',']','!','@']:
           new_name=new_name.replace(char,' ')
        new_dirname=os.path.join(root, new_name)
        print "%s --> %s"%(dirname,new_name)
        if opt.doit:
           try:
              os.rename(dirname,new_dirname)
           except OSError,err:
              failures.append("%s: FAILED to rename %s --> %s"%(err,dirname,new_dirname))
              pass

print
print "\n".join(failures)

if not opt.doit:
   print "This is just a simulation. To run this for real, use the -x flag:"
   print "    rm_spaces.py -x ~/music"
[/php]

Make it executable:
```

chmod +x rm_spaces.py
```
Use it like this:
```
rm_spaces.py ~/music      # This lists how the directories will be renamed
```

Check that the renaming is as you intend. If satisfactory, run it for real like this:
```

rm_spaces.py **-x** ~/music
```

---

### Post by ghostdog74 on 2008-09-29
you can use the Python script in my sig called File Renamer.
example usage
```

/home/music # ls -ltr
total 24
drwxr-xr-x 2 root root 4096 Sep 29 12:39 testfolder!test [artist]songtitle
drwxr-xr-x 2 root root 4096 Sep 29 12:39 testfolder@test [artist]
drwxr-xr-x 2 root root 4096 Sep 29 12:40 testfolder@testmama"sboy
-rw-r--r-- 1 root root    0 Sep 29 12:40 ordinaryfile
drwxr-xr-x 2 root root 4096 Sep 29 12:54 testfolder^test
drwxr-xr-x 2 root root 4096 Sep 29 12:56 testfolder'test

/home/music# filerenamer.py -p "[\"@\[\]]|[!']" -e "-" -t d -l "*" #use -l to list
==>>>>  [ /home/music/testfolder'test ]==>[ /home/music/testfolder-test ]
==>>>>  [ /home/music/testfolder!test [artist]songtitle ]==>[ /home/music/testfolder-test -artist-songtitle ]
==>>>>  [ /home/music/testfolder@test [artist] ]==>[ /home/music/testfolder-test -artist- ]
==>>>>  [ /home/music/testfolder@testmama"sboy ]==>[ /home/music/testfolder-testmama-sboy ]

# filerenamer.py -p "[\"@\[\]]|[!']" -e "-" -t d  "*" #remove -l to commit
/home/music/testfolder'test  is renamed to  /home/music/testfolder-test
/home/music/testfolder!test [artist]songtitle  is renamed to  /home/music/testfolder-test -artist-songtitle
/home/music/testfolder@test [artist]  is renamed to  /home/music/testfolder-test -artist-
/home/music/testfolder@testmama"sboy  is renamed to  /home/music/testfolder-testmama-sboy

# ls -ltr
total 24
drwxr-xr-x 2 root root 4096 Sep 29 12:39 testfolder-test -artist-songtitle
drwxr-xr-x 2 root root 4096 Sep 29 12:39 testfolder-test -artist-
drwxr-xr-x 2 root root 4096 Sep 29 12:40 testfolder-testmama-sboy
-rw-r--r-- 1 root root    0 Sep 29 12:40 ordinaryfile
drwxr-xr-x 2 root root 4096 Sep 29 12:54 testfolder^test
drwxr-xr-x 2 root root 4096 Sep 29 12:56 testfolder-test



```

example usage: changing first character to upper case
```

# filerenamer.py -p "^t"  -e "T" -t d  -l "*" #remove -l to commit
==>>>>  [ /home/music/testfolder-testmama-sboy ]==>[ /home/music/Testfolder-testmama-sboy ]
==>>>>  [ /home/music/testfolder-test -artist- ]==>[ /home/music/Testfolder-test -artist- ]
==>>>>  [ /home/music/testfolder-test ]==>[ /home/music/Testfolder-test ]
==>>>>  [ /home/music/testfolder-test -artist-songtitle ]==>[ /home/music/Testfolder-test -artist-songtitle ]
==>>>>  [ /home/music/testfolder^test ]==>[ /home/music/Testfolder^test ]


```

---

### Post by kingtsy on 2008-09-29
I agreed with Michaelzap. Its easier using GPRename. I have been using it to change filename download from my camera to my folder.

---

