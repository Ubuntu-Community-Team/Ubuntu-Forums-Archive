---
title: "Scripting help please"
date: 2008-10-22
forum: General Help
---

### Post by brandon88tube on 2008-10-22
I am new to linux scripting and wanted to know how to do a few things.

1. I want to know how to select all files in a folder that do not have an extension name, but not select any other files in that folder.
Ex:```
#!/bin/sh
for file in *
do
	run some command
done
```

2. I want to add Title name and Artist name to my mp3 files using the name of the file. The file is named as such "Title - Artist.mp3" <-- I really should also write a script to switch it around to the Artist - Title.mp3 so that the files all show up together based on artist if viewed alphabetically.
Ex:```
#!/bin/sh
for file in *.mp3
do
	set the first part of the filename before the space and the - to the title
set the second part of the filename after the - and space, but before the extension to the artist
done
```

---

### Post by chrisamiller on 2008-10-23
Quick and dirty answers.  There will be more than one way to achieve this:

1) This command will return all filenames that don't contain periods in the middle of the filename.  This will filter out files with extensions, but may also filter out other files, if the filename contains periods.

```
find -maxdepth 1 -type f | grep -v ".\.."
```

To do something with these files, use a little bash loop (replace echo with whatever operation you want):

```
find -maxdepth 1 -type f | grep -v ".\.." | while read line;do echo $line;done
```

To search subdirectories as well, remove the "-maxdepth 1" argument"


2) this could be done in awk or something, but here's a ruby script to do it:

```
#!/usr/bin/ruby

files = Dir.glob("*.mp3")

files.each{|file|
  arr = file.split(/\s-\s/)
  puts "mv \"#{file}\" \"#{arr[1].gsub(/\.mp3/,"")} - #{arr[0]}.mp3\""
}
```

save the code as <yourfilename>.rb, cd to the directory containing your mp3s, then run it with:

```
ruby /path/to/<yourfilename>.rb >output.sh
```

inspect the output.sh file to make sure everything looks correct, and if so, run it with 

```
bash output.sh
```


These are not the most elegant solutions ever written, but they'll do the job.

---

### Post by brandon88tube on 2008-10-23
Well how would I do it so that I also get files that have a . in the name? As I seem to have a few files without extensions, but have . somewhere in the name. Also that code is hard to understand. I saw some awk code where you just do -v and something with artist etc., but I don't know how to use it. Here is a link that has something similar [http://ubuntuforums.org/showthread.php?t=862489&highlight=mp3+artist](http://ubuntuforums.org/showthread.php?t=862489&highlight=mp3+artist)

If anyone could help me write any easy to understand script for this I would be grateful.

---

### Post by brandon88tube on 2008-10-24
Anyone? Sorry,Chris I just don't understand your code after a lot of research and I like to know what it is that I am doing.

---

### Post by chrisamiller on 2008-10-25
Really, what you're going to want to do is to read up on regular expressions.  

1)  Here's a command that will select all files without a period in the 2nd or 3rd to last position.  (ie, those without an extension)

find -maxdepth 1 -type f | awk '!/.+\.\w\w\w?/'

awk will print each line except those that match the regular expression (between slashes)  The regular expression says match:
any character (.) one or more times (+), followed by
a period (\.) which must be escaped by the slash, followed by
two alpha numeric characters (\w\w), followed by
one optional alphanumeric character.

---

### Post by chrisamiller on 2008-10-25
2) okay, lets try to clean this code up for you to make it more understandable:

```

#!/usr/bin/ruby

# get a list of all files in this directory that match
# this expression (in this case, all mp3 files)
files = Dir.glob("*.mp3")

#for each file in our list
files.each{|file|
  # take the filename and split on each instance where we see 
  # " - "  That gets stored in an array.  
  arr = file.split(/\ -\ /)

  # So, if our filename was 'foo - bar.mp3', we now have:
  #
  #  arr[0] = "foo" 
  #  arr[1] = "bar.mp3"

  # okay, now we need to strip the extension, so we use gsub to 
  # replace the ".mp3" with nothing
  arr[1] = arr[1].gsub(/\.mp3/,"")

  #now we have our elements, lets put them together
 
  newfilename =  "#{arr[1]} - #{arr[0]}.mp3"

  # in our example, this prints "bar - foo.mp3"
  puts newfilename

  # when you've reviewed the output and are sure the script works, uncomment
  # this line to actually make changes to your files

  # `mv "#{file}" "#{newfilename}"`
}

```

Save it as "mp3renamer.rb" in your home directory.  Then, cd to the directory where your files are kept, and run:

```
ruby ~/mp3renamer.rb
```

It will output a list of the new filenames.  Scroll through it, and if everything looks good, remove the comment character on the last line of the ruby script, then run it again to actually make the changes.

---

### Post by ghostdog74 on 2008-10-25
> **brandon88tube said:**
> 
2. I want to add Title name and Artist name to my mp3 files using the name of the file. The file is named as such "Title - Artist.mp3" <-- I really should also write a script to switch it around to the Artist - Title.mp3 so that the files all show up together based on artist if viewed alphabetically.
Ex:```
#!/bin/sh
for file in *.mp3
do
	set the first part of the filename before the space and the - to the title
set the second part of the filename after the - and space, but before the extension to the artist
done
```

if you don't mind a ready script, you can use the Python script in my sig called File renamer.Example usage
```

# ls -1
Title Three - Pearl_Jam.mp3
Title Two - Pearl_Jam.mp3
Title one - Pearl_Jam.mp3

# python filerenamer.py -p "(.*) - (.*).mp3" -e "\2-\1.mp3" -l "*.mp3"
==>>>>  [ /home/Title Three - Pearl_Jam.mp3 ]==>[ /home/Pearl_Jam-Title Three .mp3 ]
==>>>>  [ /home/Title Two - Pearl_Jam.mp3 ]==>[ /home/Pearl_Jam-Title Two .mp3 ]
==>>>>  [ /home/Title one - Pearl_Jam.mp3 ]==>[ /home/Pearl_Jam-Title one .mp3 ]




```
remove -l to commit

---

### Post by brandon88tube on 2008-10-25
While we are on the subject of scripts can you tell me why I keep getting the output as "filename is not flash"? Here is the code
```
#!/bin/sh
for file in *" - "*
do
	ftype=$(file "$file")
	if [ "$ftype" = "Macromedia Flash Video" ]
	then
		echo $file "is flash"
	else
		echo $file "is not flash"
	fi
done
```

---

### Post by ghostdog74 on 2008-10-25
make sure your $ftype is exactly "Macromedia Flash Player". If not, you can use expansion or regex
```

case $ftype in 
 *Macromedia* ) echo "yes";; 
esac

```
or regex (for newer bash)
```

if [ $ftype =~ "Macromedia Flash" ]

```

check the bash reference for more info.

---

### Post by brandon88tube on 2008-10-25
> **ghostdog74 said:**
> make sure your $ftype is exactly "Macromedia Flash Player". If not, you can use expansion or regex
```

case $ftype in 
 *Macromedia* ) echo "yes";; 
esac

```
or regex (for newer bash)
```

if [ $ftype =~ "Macromedia Flash" ]

```

check the bash reference for more info.


The second one didn't work. It says [: 11: =~: unexpected operator

---

### Post by ghostdog74 on 2008-10-25
use double square brackets. Check the bash reference or the link in my sig for more info on how to use regex operator =~

---

### Post by brandon88tube on 2008-10-25
Sorry, I have been reading up on bash scripting and only a little bit is sinking in. I tried double brackets like you said and I still get an error.

---

### Post by geirha on 2008-10-25
The reason for those errors is the first line which reads #!/bin/sh. Your script is using bash syntax, so you should change the shebang to #!/bin/bash, so it gets interpreted by bash and not sh.

On the issue with mp3-files, I recommend you try [tagtool](apt://tagtool) which is a gui application that fairly easily can set tags based on filenames and vice versa.

---

### Post by brandon88tube on 2008-10-25
> **geirha said:**
> The reason for those errors is the first line which reads #!/bin/sh. Your script is using bash syntax, so you should change the shebang to #!/bin/bash, so it gets interpreted by bash and not sh.

Yeah, thanks that worked. Man I really don't know this stuff enough to really use it.

---

