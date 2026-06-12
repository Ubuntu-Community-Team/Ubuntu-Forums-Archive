---
title: "battery died and interrupted update (my solution)"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by nmz787 on 2008-12-15
so my battery died while the update manager was processing updates.

first i copied /var/log/dpkg.log to my working directory
  
```
sudo cp /var/log/dpkg.log ./
```

then i sorted this list according to the date i did the updates on

```
cat dpkg.log | grep 12-10 > newfile.file
```

then i wrote this perl script to parse through newfile.file stripping the everything but the package name, and print the list to the screen.

in my case i wanted to reinstall everything on this list, with some exceptions (i commented these areas in the script), so I piped the list to apt-get

```
sudo apt-get install --reinstall `perl sortDpkg.pl`
```


it took me a while to get it to work, I had to purge some apache packages manually
```
sudo dpkg --purge package-name
```

these are also helpful if your system packages are out of order:

to reconfigure the last install (if the config step died)
```
sudo dpkg --configure -a
```

try to have apt-get fix itself after a crash/issue:
```
sudo apt-get install -f
```



```
#!/usr/bin/perl
use strict;
#open the file newfile.file (you can change this to whatever you filename is)
open(MYINPUTFILE, "<newfile.file");

my @pkgArray = ();
my $firstTime=1;

#loop through every line in the file and parse the package name out of it
while (<MYINPUTFILE>){
 my($line) = $_;
 chomp($line);
 my $newIndex=rindex($line, "installed");
 my $newli = substr $line, $newIndex + 10;
 $line = substr $newli,0, index($newli, " ")+1;
  
  my $noDuplicate = 1;
  #go through the list to see if there are duplicate entries
  for (my $i = 0; $i < scalar(@pkgArray); $i++) {
   if ( @pkgArray[$i] eq $line ) {
   	$noDuplicate = 0;
   }
  }
  #if there are no duplicates proceed to push a package from the file into the list
  if ( $noDuplicate ) {
   #check to make sure "installed" was found in the parsed line, if not value will be -1
   #this is because the package name follows "installed" in the string
   if ($newIndex>=0) {
    #remove or add packages and exceptions (for things like version conflicts)
    if ($line eq "package-name-to disclude " | $line eq ""){
    } else {
     #these are examples of when the list had packages that apt-get told me needed to be newer versions
     if ($line eq "libgail18 ") { 
      push(@pkgArray,"libgtk2.0-0 ");
     } elsif ($line eq "libgmime-2.0-2 ") { 
      push(@pkgArray, "libgmime-2.0-2a ");
     } else {
      #if there are no exceptions, this is the main line for building the list
      push(@pkgArray, "$line");
     }
    }
   }
  }
}

#print each element in the package list, with a newline character for readability, etc...
foreach (@pkgArray){
 print($_,"\n");
}
```

---

