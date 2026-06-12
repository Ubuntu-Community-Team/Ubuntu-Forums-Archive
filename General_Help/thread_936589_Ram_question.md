---
title: "Ram question?"
date: 2008-10-02
forum: General Help
---

### Post by Vertoxic on 2008-10-02
ok guys so i decided to stick with ubuntu i just got 32 bit, and i was told my laptop would read 4 gigs, but it only reads

toliy@toliy-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3106704     793236    2313468          0      44036     325036
-/+ buffers/cache:     424164    2682540
Swap:      7960168          0    7960168
toliy@toliy-laptop:~$ 

is thats how its going to be unless i go back to 64 bit?

---

### Post by binbash on 2008-10-02
you have to install server kernel if you want more than 3 gb ram

---

### Post by OutOfReach on 2008-10-02
As far as I know, 32 bit operating systems support only 3GB of RAM. But I think that you can make it use all of the RAM, I'm just not sure of the technique.

EDIT: binbash has got it right, you need to install the server kernel to make use of the full ram.

---

### Post by Vertoxic on 2008-10-02
> **binbash said:**
> you have to install server kernel if you want more than 3 gb ram
ok sweet how do i do that?

---

### Post by 3rdalbum on 2008-10-03
It doesn't matter - you're not likely to be running a database server or scientific calculations on a laptop, so it's **extremely** unlikely you'll hit 3 gibibytes of RAM use, much less 4.

I opened Flock, Pidgin, Google Earth, The Gimp (4 megapixel image), Krita (4 megapixel image), Openoffice.org (spreadsheet), Inkscape, F-spot, and Evolution simultaneously. It used 898 MiB actively, and 600MiB cache, making a grand total of 1.5GiB used.

If you're likely to run over twice as many big programs as that simultaneously, then by all means install the server kernel or go 64-bit. Otherwise, it simply doesn't matter at this stage.

---

### Post by Vertoxic on 2008-10-03
well what is a server kernel?

---

### Post by binbash on 2008-10-03
sudo apt-cache search linux image server

---

### Post by Vertoxic on 2008-10-03
> **binbash said:**
> sudo apt-cache search linux image server
just ranned that command, restarted my pc still 3 gigs reads.
i want my 4 gigs :(

             total       used       free     shared    buffers     cached
Mem:       3106704     741228    2365476          0      13152     291312
-/+ buffers/cache:     436764    2669940
Swap:      7960168          0    7960168

---

### Post by binbash on 2008-10-03
No dude, i have additional repos in my sources.list ,so i dont know if you have my packages or not.

Give this command :

sudo apt-get install linux-image-server

And install it then make sure you booted with that kernel (select server kernel at grub)

---

### Post by Vertoxic on 2008-10-03
> **binbash said:**
> No dude, i have additional repos in my sources.list ,so i dont know if you have my packages or not.

Give this command :

sudo apt-get install linux-image-server

And install it then make sure you booted with that kernel (select server kernel at grub) 
k i just did that it download a 77 mb and when i started in in server kernel it loges in and then the screen stays all white... loads just fine just after login it stays white :(
btw i dont have any respos at all what do i need to fix that?

---

### Post by cariboo on 2008-10-03
Check out this link:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

and build yourself a custom kernel that will use all of your ram. Or install the 64bit version.

Jim

---

### Post by Vertoxic on 2008-10-03
> **cariboo907 said:**
> Check out this link:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

and build yourself a custom kernel that will use all of your ram. Or install the 64bit version.

Jim
yah ill prolly go back to the 64 bit V, its just alot harder then the 32 bit one, lol well thx anyways! i appreciate ur help!

---

### Post by 3rdalbum on 2008-10-03
Dude, I'm telling you, you do not need to address all 4 gigabytes of RAM with Ubuntu.

Just for you, [I ran a test]("http://bigbolshevik.blog.friendster.com/2008/10/the-overkill-one-or-the-ridiculously-overkill-one/"): Could I fill up all my 2 gigabytes of RAM? It took 43 programs, each loaded with a significant amount of data (for instance, image files in the image editors). In fact, my computer crashed before hitting the 2 gigabyte mark, because my graphics card didn't have enough onboard memory to render all the windows!

Dude, you're never going to hit 3 gigabytes of RAM use on Ubuntu, much less 4. If you want to install 64-bit, which is the proper solution to the problem, then go ahead. But fiddling around with PAE on server kernels is the difficult solution to a problem you'll never run into.

---

### Post by hyper_ch on 2008-10-03
Is there a reason why you're not using 64bit?

---

