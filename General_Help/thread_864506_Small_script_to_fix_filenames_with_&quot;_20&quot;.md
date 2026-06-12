---
title: "Small script to fix filenames with &quot;_20&quot; instead of spaces"
date: 2008-07-19
forum: General Help
---

### Post by Labyrinth on 2008-07-19
I wrote this for my own convenience when I had a lot of files with their names garbled like "bla_20this_20is_20a_20weird_20looking_20filename.html".

Such weird names are produced when a filename is first urlencoded and then the %-signs replaced with "_" to be more compatible with some file systems.

Here's the script's code:
```
#!/usr/bin/python
# -*- coding: utf-8 -*-

# Licensed under the GPL
# Written by Klaus Bitto
# Version 0.1 from 2008-07-19

# Version history:
#
# 0.1 2008-07-19
# Initial release

#    urldec.py - fixing weird_20filenames.ext arguments are directories in 
#    which you want to fix the files. 

#    Copyright (C) 2008 Klaus Bitto (firstname.lastname@gmail.com)
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#

import os, sys, urllib, os.path

def handle_dir(target_dir):
	oldnames = [e for e in os.listdir(target_dir)] # if e.endswith(".mp3")
	newnames = [unicode(urllib.unquote(e.replace("_","%")),encoding="latin1") \
		for e in oldnames]
	for i, old in enumerate(oldnames):
		os.rename(os.path.join(target_dir, old), os.path.join(target_dir, newnames[i]))

def main():
	if len(sys.argv) < 2:
		print "Needs a dir to work on. Try giving \".\" as argument."
		sys.exit(0)
	map(handle_dir, sys.argv[1:])
			
	
if __name__ == "__main__":
	main()
```

Copy, save to your home folder as "urldec.py", make executable, and call from the terminal.

If you are inside the directory with the garbled file names, call "~/urldec.py ." (Don't forget the dot!)

Otherwise you can give as many directories as you want as arguments. E.g. "~/urldec.py somedir some/path someotherdir"
In all given directories, filenames with non-ascii characters encoded as "_NN" will be fixed.

If you are not in a latin1 zone, and you get errors (UnicodeDecodeError) while executing, try replacing "latin1" in the source code with your local encoding - or whichever encoding the garbled filenames might be in.

Would be nice if someone could confirm that this is no malicious code...

Otherwise - have fun! :guitar:

---

### Post by nick_h on 2008-07-20
> Would be nice if someone could confirm that this is no malicious code...

I can confirm that this is not malicious code. It looks like it should work.

---

