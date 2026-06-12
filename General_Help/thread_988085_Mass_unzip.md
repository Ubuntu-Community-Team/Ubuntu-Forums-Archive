---
title: "Mass unzip"
date: 2008-11-20
forum: General Help
---

### Post by Phreaker on 2008-11-20
I have a bunch of zip packages in one folder and I want to unzip them to another.
How can I do that?

---

### Post by rampageoberon on 2008-11-20
a shell script perhaps with unzip prepended to every line of the file list

```
#!/bin/bash

unzip file1
unzip file2
```

---

### Post by Phreaker on 2008-11-20
Is there an easier way.I am talking about 50+ zip files

---

### Post by ajgreeny on 2008-11-20
My very simple mind suggests this as a possibility.  Can you use a * as wildcard?

```
#!/bin/bash

unzip *.*
```I have no idea if it will work, but it must be worth trying.  You don't even need to use a script, as far as I can see.

---

### Post by jigsaws on 2008-11-20
```
find . -type f -name "*.zip" -exec unzip '{}' \;
```

---

### Post by rampageoberon on 2008-11-20
yes the 2 suggestions above will work

alternatively you can run the perl script below with the correct details.

```
#!/usr/bin/perl

my $inputdir = "/your/dir/with/zip/files";
my $outputdir = "/dir/for/output/files";

opendir(DIR, $inputdir) or die("Can not open directory");

@files = readdir(DIR);

foreach $index (@files){
        if ($index eq "." || $index eq "..") { }
        else {
                `unzip -d $outputdir $index`;
        }
}
```

hope that helps

---

### Post by malachi on 2008-11-20
I'm sure you can also select all of the .zip files, right-click, and choose "Extract Here."

(I'm not sure if that's what you want, though.)

---

