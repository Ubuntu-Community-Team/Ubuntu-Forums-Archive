---
title: "Perl in Ubuntu"
date: 2008-09-01
forum: General Help
---

### Post by danbrownlow on 2008-09-01
Hey there, I've been learning perl recently and I came across these tutorials written for Perl version 5.1. 

According to perl -v I'm using perl 5.8.8 so I'm wondering how do I get these programs to work?

This is a piece of code that demonstrates:

```

#!usr/bin/perl;

use feature ':5.10';
say "Hi there!";

```

I know this isn't a programming section, but I'm not really asking about coding, just about how to run the perl haha. Sorry if this is the wrong section.

Dan.

---

### Post by Mister.Vash on 2008-09-01
If you are looking to use 5.10, you may want to try Intrepid rather than hardy.  Keep in mind that intrepid is still beta.  See the following thread:
[http://ubuntuforums.org/showthread.php?t=852752](http://ubuntuforums.org/showthread.php?t=852752)



The forums do have a programing section that can help with examples, questions, etc.
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)



If you do get going with the 5.10, the code that you posted did have a typo:
#!usr/bin/perl;
Is actually a path to the interpreter so it should have the slash at the start - so it should be
#!/usr/bin/perl




If you just want to get going with perl, and are not concerned about the specific features of 5.10, you can get up and running with the following:

Save the following text into a new text file, you can name it anything you want, I'll just call it test.pl
[PHP]
#!/usr/bin/perl

print "Hi there!";

[/PHP]
Once you have the file saved, open a terminal, change to the folder that you saved the file to and then do the following which makes the file executable:
```

chmod +x test.pl

```

And the following will run the file from the current directory
```

./test.pl

```

---

### Post by danbrownlow on 2008-09-01
Hey there, yea', I'm writing it like that now thanks. Was just reading into 5.1 and wanted to try it out =]

Anyway, how come you use the chmod? I normally just run it as "perl test.pl"

Just wondering ^_^

Dan.

---

### Post by Mister.Vash on 2008-09-01
You can do either way based on preference.  chmod can save you a bit of typing, especially if you write something that you end up using a lot.

---

