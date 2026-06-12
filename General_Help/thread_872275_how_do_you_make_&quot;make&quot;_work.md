---
title: "how do you make &quot;make&quot; work?"
date: 2008-07-27
forum: General Help
---

### Post by harryliddic on 2008-07-27
I have no troubles configuring a file but when I type 'make' I always get the error message 'no makefile can be found' this has limited my use of crucial apps. I have checked the Synaptic and 'make' is marked. when I put the makefiles as arguments I get "nothing can be done with this file" Is this systemic or me?

---

### Post by cheetaux on 2008-07-27
What is it that you are trying to build?

make, by default, expects as an input a file called "makefile".  Is there a file called makefile in the directory where you are trying to execute make?

---

### Post by iaculallad on 2008-07-27
> **harryliddic said:**
> I have no troubles configuring a file but when I type 'make' I always get the error message 'no makefile can be found' this has limited my use of crucial apps. I have checked the Synaptic and 'make' is marked. when I put the makefiles as arguments I get "nothing can be done with this file" Is this systemic or me?

Change directory to make's location:

```
cd make_location
```

then:

```
sudo ./make
```

or

```
./make
```

---

### Post by harryliddic on 2008-07-27
I am trying to build the lastest version of Kino. Why is another whole kettle of fish.
I am using make in the same directory as two files 'Makefile.in' and 'Makefile.am' when I put these two as input it says 'there is nothing to do with them'

---

### Post by sengines on 2008-07-27
If you are trying to compile kino make sure you have build-essential

sudo apt-get install build-essential


latest kino is kino-1.3.0.tar.gz

to untar
tar -zxvf kino-1.3.0.tar.gz

change to kino directory

cd kino-1.3.0

sudo apt-get build-dep kino

sudo ./configure (--prefix=/usr etc if you want it compiled to a certain location and a certain way)

sudo make

sudo make install

---

### Post by harryliddic on 2008-07-27
harry@harry-desktop:~/kinodv/kino-1.3.0$ make
make: *** No targets specified and no makefile found.  Stop.
harry@harry-desktop:~/kinodv/kino-1.3.0$ ./make
bash: ./make: No such file or directory
harry@harry-desktop:~/kinodv/kino-1.3.0$ cd make_command
bash: cd: make_command: No such file or directory
harry@harry-desktop:~/kinodv/kino-1.3.0$ cd make_location
bash: cd: make_location: No such file or directory
harry@harry-desktop:~/kinodv/kino-1.3.0$ sudo ./make
[sudo] password for harry: 
sudo: ./make: command not found
harry@harry-desktop:~/kinodv/kino-1.3.0$ make Makefile.in Makefile.am
make: Nothing to be done for `Makefile.in'.
make: Nothing to be done for `Makefile.am'.
harry@harry-desktop:~/kinodv/kino-1.3.0$ 


what is my problem?

---

### Post by sengines on 2008-07-27
how bout sudo make

read my instructions above

---

### Post by ceclauson on 2008-07-28
"make" won't be able to work unless there's a file named "Makefile" in the current directory.  From the output above, I'm guessing it's not there.

Usually in source distributions, there's a script that you have to run first to generate the makefile.  Usually it's called "configure".  See if there's a file called "configure" in the directory.  If so, execute it by typing "./configure" at the prompt.  If all goes well, you should end up with a makefile, and can then use "make" to build the project.

After you've built the project, you can usually install it by typing "sudo make install" at the prompt.  If the "configure" file isn't there, you'll probably need to read the instructions for building the project, either on the project website, or in a file in the directory.

-Cooper

---

