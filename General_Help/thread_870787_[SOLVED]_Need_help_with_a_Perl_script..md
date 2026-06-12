---
title: "[SOLVED] Need help with a Perl script."
date: 2008-07-26
forum: General Help
---

### Post by peterswinkels on 2008-07-26
At [http://ubuntuforums.org/showthread.php?t=495131&page=5](http://ubuntuforums.org/showthread.php?t=495131&page=5) I found the following Perl script which is supposed to open Microsoft Internet Explorer shortcuts with Firefox in Ubuntu Linux:

```

#!/usr/bin/perl

# Script to make Microsoft Windows Internet Shortcuts (*.url) work on Linux. 

# Oomingmak fixed version. This script now works properly.
# It no longer cuts off the last character of the URL.

# Open up the file
open(F,"<$ARGV[0]") or die "$0: Could not load Internet Shortcut file $ARGV[0]!\n";

# Find the URL
while($in = <F> and not $url) {
    chomp($in);
    if($in =~ m/\s*URL\s*\=\s*\S*\s*\015*/) {
        $url = $in;
    $url =~ s/\s*URL\s*\=\s*//; # Filter out the beginning stuff
    $url =~ s/\s*\015+//; # Filter out the nasty DOS carriage return!
        
        
    }
}

    system "firefox $url &";# or die "$0: Could not open $netscape\n"

```

Now, the problem is that this script doesn't appear to ignore BASEURL=*URL* entries, causing it to attempt to open Firefox with the URL BASE*URL*. If an Internet Explorer shortcut file contains, for example, "BASEURL=http://vbforums.com", the script will interpret this as "BASEhttp://vbforums.com".

So, my question is: How do I get the script to ignore BASEURL entries? Since I don't know anything about Perl, I can't change the script myself.

Thanks in advance.

BTW:
I'm starting a new thread here since I can't reply to the one where I found the script.

---

### Post by peterswinkels on 2008-07-27
I decided to write my own script for Bash. It works with the shortcuts I was having trouble with using the Perl script.

My own script:
```

#!/bin/bash
# OpenIEURL - by: Peter Swinkels, ***2008***
# This script opens the URL in the specified Microsoft Internet Explorer shortcut (*.url file) using Firefox in Linux.

# This procedure processes the data in the shortcut file.
# It waits until it finds the "InternetShortcut" section header.
# It then launches Firefox with the first URL that is preceded by "URL=".
# After that, it closes with exit code 0.
# If no header or URL is found, the script closes with exit code 1.
function ProcessLine ()
{
	if [ "$FoundUrlHeader" -eq "0" ]; then	
		if [ "${1:0:18}" == "[InternetShortcut]" ]; then FoundUrlHeader=1; fi
	else
		if [ "${1:0:4}" == "URL=" ]; then
			firefox "${1:4}";
			exit 0;
		fi
	fi
}

# Script entry point.
# Feeds each line in the shortcut file to the ProcessLine procedure.

FoundUrlHeader=0;	# This variable indicates whether the "InternetShortcut" section header has been found.

for Line in `cat "$1"`; do ProcessLine "$Line"; done
exit 1;

```

If you have suggestions/comments or found a bug, please let me know.

---

