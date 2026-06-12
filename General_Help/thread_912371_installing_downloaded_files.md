---
title: "installing downloaded files"
date: 2008-09-06
forum: General Help
---

### Post by Unlearned on 2008-09-06
i download a tar.gz to Documents and wanted to install it, but when i tried to use synaptic the file is grey and cannot be selected to install
how do i get files like this to install

---

### Post by zipperback on 2008-09-06
> **Unlearned said:**
> i download a tar.gz to Documents and wanted to install it, but when i tried to use synaptic the file is grey and cannot be selected to install
how do i get files like this to install



Open a terminal window (Applications -> Accessories -> Terminal )

change to the directory where you downloaded the file to.

Example:   cd /home/username/downloads

Now you have to uncompress the file that you downloaded.

tar xvfz filename.tar.gz

Replace filename with the actual name of the file that you downloaded.

Then change into the directory that tar just created.

cd directory_name

Replace directory_name with the actual directory name.

Now look and see if there is a README or an INSTALL file.

Read it and follow the instructions.

Also, you should check the repositories and see if the application is available as an ubuntu package. 

You can launch synaptic and search for the application or you can do it from the terminal window with the following:


sudo apt-get update & sudo apt-cache filename

replace "filename" with the actual application that you want.

This will bring up a list of results, then you can just install the one that you want. From the command line it is as follows:

sudo apt-get install filename

Again, replace "filename" with the actual package name that you want to install.

It is best to always install from an official repositoy whenever possible.


- zipperback
:popcorn:

---

### Post by Elfy on 2008-09-06
It could need to be compiled to install it. First are you sure that a .deb is not available for the program.

That aside you need to make sure you have build-essentail installed, using checkinstall cna be a help as well, so from a terminal

```
sudo apt-get install build-essential checkinstall
```

To install it you would need to extract

```
tar -zxvf filename
```

change to directory then start to compile
```
./configure
make
sudo make checkinstall
```

---

### Post by hyper_ch on 2008-09-06
isn't it in the repos or on getdeb.net?

---

