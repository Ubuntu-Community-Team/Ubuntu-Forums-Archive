---
title: "default download directory"
date: 2008-07-11
forum: General Help
---

### Post by silentbob1978 on 2008-07-11
Hi

I have just installed server 8.04 and I have downloaded a file using the wget command line.  I was unable to specify a download location so how do I find it.

I am just learning ubuntu at the moment so assume I am stupid

---

### Post by damis648 on 2008-07-11
> **silentbob1978 said:**
> Hi

I have just installed server 8.04 and I have downloaded a file using the wget command line.  I was unable to specify a download location so how do I find it.

I am just learning ubuntu at the moment so assume I am stupid

Use the following syntax:
```
wget http://place.com/file /download/directroy
```

---

### Post by silentbob1978 on 2008-07-11
Here is what typed based on the response above

wget [http://download3.vmware.com/software/vmserver/VMware-server-1.0.5-80187.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.5-80187.tar.gz) /src/VMWare

is this correct as it downloads the file then I get the error

/src/VMWare: Unsupported scheme.

any ideas

---

### Post by joshsmith on 2008-07-11
to find out how something works, and what options are needed, run 
{name of command} --help
and
man {name of command}

so in this case
wget --help
and 
man wget
tells you about all of the options you can give wget including the one to choose where you save a file to (if a location is not specified it downloads to the current directory)

---

### Post by unutbu on 2008-07-11
```
wget http://download3.vmware.com/software...5-80187.tar.gz -O /src/VMWare
```

would download a url to /src/VMWare. Without the -O flag the wget command downloads the url into the current working directory.

---

### Post by damis648 on 2008-07-14
> **unutbu said:**
> ```
wget http://download3.vmware.com/software...5-80187.tar.gz -O /src/VMWare
```

would download a uri to /src/VMWare. Without the -O flag the wget command downloads the uri into the current working directory.

Don't you mean URL?

---

### Post by unutbu on 2008-07-14
Yes, thanks; I should have said URL.

---

### Post by satyaanveshi on 2008-09-28
Just out of curiosity, can I change the  defualt download directory for wget?

---

### Post by unutbu on 2008-09-28
wget usually downloads into the current working directory.

So you have two choices:

```
cd /src/VMWare
wget http://download3.vmware.com/software/vmserver/VMware-server-1.0.5-80187.tar.gz

```
or 
```

wget http://download3.vmware.com/software/vmserver/VMware-server-1.0.5-80187.tar.gz -O /src/VMWare


```

---

### Post by satyaanveshi on 2008-09-28
Thanks for a quick reply. :)

---

