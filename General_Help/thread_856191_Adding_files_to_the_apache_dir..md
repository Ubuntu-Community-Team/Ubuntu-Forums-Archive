---
title: "Adding files to the apache dir."
date: 2008-07-11
forum: General Help
---

### Post by painejake on 2008-07-11
I run a website and i want to change from Windows Server 2003 to Ubuntu 8.04 (do i need a reason? lol) and i have installed MySQL, PHP5 and Apache fine under ubuntu desktop but i can seem to add files/webpages into my www directory in /var/www/

Everytime i try to move a file there it fails. I have heard of Chmodd or something like that. Does that have anything to do with my problem? I have little experience on Linux but i will try my best if anyone has any suggestions or know what to do. 

Many thanks!!

Jay :)

---

### Post by justleen on 2008-07-11
by default, the /var/www/ directory is owned by root. So only root can place files there (thus, instead of "cp <files> /var/www/" you need "sudo cp <files> /var/www/")

If you want your normal user to place files there, you can change the ownership.
```
 sudo chown -R user:user /var/www/
```
-R for recursive
user:user is the new owner:group

---

### Post by MasterXandrex on 2008-07-11
Firstly, I would not recommend changing the ownership of /var/www until you know what you are doing, this can very easily cause a security risk.

These are terminal directions -- because if you are going to use linux, you should get to know the terminal -- and some of these things are easier in the terminal.

Ok, linux uses a strict permission structure and here are the basics:

All files, folders, and links have an owner and a group and then permissions are set based on what the owner can do, what the group can do, and what everyone can do. 

If you'll run the command:

```

ls -l /var/

```

(this stands for **l**i**s**t **l**ong format) you'll find this line:

```

drwxr-xr-x  4 root root  4096 2008-06-30 21:54 [COLOR="DeepSkyBlue"]www[/COLOR]

```

From left to write, here is what this means:

the d indicated the file type -- directory
the next 9 characters is called the permission mask and it comes in groups of three -- this lists what each category can do. Read and write are fairly straight forward. Execute, if it is a folder, means that the category has the ability to execute commands inside the folder; if it is a file, then it means the category has the ability to execute the file.
   the first three are for the owner -- in this case **r**ead, **w**rite, and e**x**ecute.
   the next three are for the group -- in this case **r**ead and e**x**ecute
   the final three are global -- in this case **r**ead and e**x**ecute
The next piece is the directories number, telling the amount of directories in the directory  (including . and ..)
The next piece is the owner, in this case root.
The next piece is the group, in this case also root.
The next piece is the size in bytes (add the -h flag for human readable numbers) this does not tell you the size of all the files inside a folder, only the size of the folder itself.
The next piece is the Date it was last modified (again in the case of folders, the folder itself, not the contents)
The final piece is the name of the file or folder it's listing

Now, this is a pretty standard setup for a /var/www apache folder, so I do not recommend changing the permissions on it. Instead, what you are looking for is the "sudo" command (**S**uper **U**ser **DO**). It allows you to issue on command as root (the god-admin in linux). This will basically let you do anything -- so be careful. 

What you will want to do is this:
```

sudo mv /path/to/index.html /var/www

```
This will move /path/to/index.html (which should be replaced with your file) to /var/www.

You will then need to make sure it is setup so apache and anyone else can read it when necessary. So you will want to "chmod" (**Ch**ange **Mod**e) it. 

```

sudo chmod 755 /var/www/index.html
755 is a representation of the permission mask and here is how it works
read is 4
write is 2
and execute is 1
if you want the owner to have read and write and execute that's a 7
if you want the group to have only read and execute that's a 5
if you want everyone else to have nothing that's a 0

```

This is necessary for most files in this directory so apache can read them and not be the owner. 

That should get you started, you might want to pick up a book or "acquire" and eBook.

One other thing I want to point out to you is the recursive flag which is needed for some commands when working with directories: "cp" (**c**o**p**y) and "chmod" being among them.

```

sudo chmod -R 755 /var/www/

```
Will set all files in /var/www to the mask


```

sudo cp -r /path/to/directory/ /var/www/

```
Will copy "directory" directory and all subfiles and subdirectories to /var/www

You can learn much more about these commands by typing 
```

man cp

```
and replace cp with whatever you want to learn about

If you don't know a command you may be able to mind it by typing
```

apropos move

```
Where move is replaced with one word for what you want to do. In this case the output is:

```

mv (1)               - move (rename) files
XGetIMValues (3)     - open, close, and otain input method information
XGetOMValues (3)     - open output methods
XrmValue (3)         - initialize the Resource Manager, Resource Manager stru...
XSetIMValues (3)     - open, close, and otain input method information
XSetOMValues (3)     - open output methods
XVisualIDFromVisual (3) - obtain visual information and visual structure

```
and obviously one would use the first one.


Let me know if you need any clarification,


Xan

---

### Post by js_fr on 2008-07-11
you can simply add an alias in your httpd.conf file and tell Apache to look in a folder of your home directory. To do this edit httpd.conf ... ```
gksudo gedit /etc/apache2/httpd.conf
```
and add the following ... ```
Alias /youralias /home/your_username/public_html
```
replace /youralias and your_username/public_html with something that's appropriate for you
You can then access files that you put under /home/your_username/public_html with [http://[your](http://[your) server name]/youralias

If you don't like to have something like /youralias in your pathname you can define a vitual host. A good description how to do this you can find here: 
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Adding_a_virtual_host_to_your_LAMP_server]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Adding_a_virtual_host_to_your_LAMP_server")

PS:
Of course you have to make sure that apache can access the directory you defined in your Alias / Virtual host. That means this directory (and the ones above) should have 755 permissions.

---

### Post by painejake on 2008-07-11
Thankyou very much Van thats a really detailed guide. So Chmod is basically the mode of who can access my files over my web server. So could i have 744 instead of 755 as surly that would be more secure or am i wrong? Thanks to you other guys too :)

---

### Post by MasterXandrex on 2008-07-11
Well that depends you can 744 individual files and it will work but you need to have execute permissions on the folders for apache to be able to execute commands inside the folders (like listing and finding the files). 

In short, it's not that much of a security benefit to remove execute. Also you don't need to worry (atleast in this context) about the security from people viewing your webpage. The file system security is mostly for other users on the system.


Xan

---

### Post by painejake on 2008-07-16
Could i ask you one more thing? Im tring to install php fusion. I keep getting this error though:

```

Warning: fopen(config.php) [function.fopen]: failed to open stream: Permission denied in /var/www/setup.php on line 162

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/setup.php on line 163
Unable to write to config
Please check write permissions and restart setup.

Warning: fclose(): supplied argument is not a valid stream resource in /var/www/setup.php on line 165
```

I think its the chmod but im not 100% sure. I've tried chmod'ing the /var/www/setup.php using the command

```
sudo chmod -R 755 /var/www/setup.php
```

and it seems to work fine as i get no errors. But still it is not working i also tried 

```
sudo chmod -R 755 /var/www/
```

But that also has bot not worked. Many Thanks

---

