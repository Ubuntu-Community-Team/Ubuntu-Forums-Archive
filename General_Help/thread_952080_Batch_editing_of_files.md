---
title: "Batch editing of files"
date: 2008-10-18
forum: General Help
---

### Post by blis102 on 2008-10-18
Hello everyone!

Im not sure if I posted this in the right place but here goes...

I am a beginner with Linux/Unix and am wondering how I can take a group of files in a directory and run some regular expression function (say, to take out a specific section of the file, between certain HTML tags) and append all of them to one file. For example, I have these files:

```
files/
[INDENT]foo.html
bar.html
foobar.html
foofoo.html
barbar.html[/INDENT]
```

...and each file is structured similarly (basic HTML) and I would like to take out everything between the <body> tags and put them into a file somewhere else (or even a database using SQL syntax), lets say called results.sql. It would also be ideal to format the results (I assume using REGEX would do the trick). 

My question is, what Linux commands can I do to accomplish this and how would I go about doing it (links to tutorials would be great)? Would I need to write code, like Python or something else to accomplish this?

Thanks a ton!

---

### Post by tCarls on 2008-10-21
To run commands on multiple files I usually do something like this:
```
for file in files/*.html; do some_command $file; done
```

The trickiest part would be filtering the files to remove everything not in body tags. I don't think you could just use regular expressions for that. Here's a short perl script I wrote that seems to work well enough:

```

#!/usr/bin/perl -w
# filter.pl
use strict;

my $in_body = 0;

foreach my $line (<>) {
        if ($line =~ /<body>/i) {
                $line =~ s/.*<body>//i;
                $in_body = 1;
        }
        if ($line =~ /<\/body>/i) {
                $line =~ s/<\/body>.*//i;
                print $line;
                $in_body = 0;
        }
        print $line if $in_body;
}

```

Use it like this:
```
for file in files/*.html; do ./filter.pl < $file; done > out.html
```

---

### Post by blis102 on 2008-10-21
@tCarls

Thanks a lot for the reply. I will try that out today! Thanks!

---

