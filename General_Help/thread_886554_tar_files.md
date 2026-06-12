---
title: "tar files"
date: 2008-08-11
forum: General Help
---

### Post by deeds3353 on 2008-08-11
when i download a bzip or gzip or any tar file i save it on desktop. Thats easy, however can any one give me a simple step by step process to extract and install this kind of file??????? I am new to linux so please be gentle.......... Thanks...:(:confused:

---

### Post by hyper_ch on 2008-08-11
what have you tried so far to find a solution for that problem?

---

### Post by Mikes80 on 2008-08-11
Right-click on the tar file. In the menu you'll seen an option to extract it. IIRC (running xubuntu at the moment) there'll be two option one to extract here (the current directory) and one to extract to another destination.

As for installing the tar. You'll need to provide a bit more information about what the file is.

Hope the helps :)

---

### Post by AxiomShell on 2008-08-11
> **deeds3353 said:**
> when i download a bzip or gzip or any tar file i save it on desktop. Thats easy, however can any one give me a simple step by step process to extract and install this kind of file??????? I am new to linux so please be gentle.......... Thanks...:(:confused:

You can open a terminal and write:

```

tar xzf downloaded_file.tar.gz

```

where **downloaded_file.tar.gz** is the actual name of the file you downloaded.
If you saved it to the desktop, the file is probably on **~/Desktop**

---

### Post by pparks1 on 2008-08-11
As an example, filename.tar.gz.

The .gz portion tells you that the file is compressed with gzip.   You can unzip with gunzip filename.tar.gz.

The .tar portion tells you that you have a tape archive file.  It's a collection of multiple files, packaged into 1 single file, but without compression.

You can untar the file with tar -xvf filename.tar.   (-x is for extract)

You can create your own tar file with tar -cvf filename.tar /sourcedirectory/*.*


Also, the tar command knows how to handle the compression, so you can gunzip and untar with the same command

tar -xzvf filename.tar.gz  (the -z is for gunzip)

---

