---
title: "Installing OpenCL on Lucid"
date: 2010-07-21
forum: Hardware
---

### Post by slow photon on 2010-07-21
Hello All, 

I am a new user of Ubuntu and I am trying to install OpenCL on the Lucid version. I am working to integrate my HD 5770 GPU into some of my code by using OpenCL. 

I am wondering if there are any installation guides for OpenCL on Ubuntu or if anybody has successfully done this. 

My system contains: 

AMD Phenom 9500
ATI HD 5770 
Ubuntu 10.04 64 bit distribution

---

### Post by kutya61 on 2010-08-15
Hi!
As I know this is the only way, you can use OpenCL on linux with ATI Graphics Card.

On [this]("http://developer.amd.com/gpu/atistreamsdk/pages/default.aspx") site you can download ATI Stream SDK for linux. Unpack the downloaded file somewhere in your home directory.

You have to download the [icd-registration.tgz]("http://developer.amd.com/Downloads/icd-registration.tgz") file also, and extract it into the root directory:
```
cd /
sudo tar xzf /path/to/file/icd-registration.tgz
```
This will unpack 2 files in the /etc/OpenCL/vendors directory.

Second, put these lines in your .bashrc:
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH":/path/to/ati-stream-sdk-v2.2-lnx32/lib/x86/"
export LIBRARY_PATH=$LIBRARY_PATH":/path/to/ati-stream-sdk-v2.2-lnx32/lib/x86/"
export C_INCLUDE_PATH=$C_INCLUDE_PATH":/path/to/ati-stream-sdk-v2.2-lnx32/include/"

```
Of course you have to change the "/path/to" things. These environmental variables are for 32 bit linux, figure it out for 64bit.

After this in the C file you have to include
```
#include <CL/opencl.h>
```
In example OpenCL sources there are other variations for the include file, like OpenCL/OpenCL.h or CL/OpenCL.h, but never mind.

Now you can simply compile with
```
gcc source.c -o prog -lOpenCL
```
Here you need a new terminal in order to let bash know the changes in the .bashrc.
If you do not set the environmental variables you have to tell the compiler where are the needed files with
```
gcc source.c -o prog -I /path/to/ati-stream-sdk-v2.2-lnx32/include -L /path/to/ati-stream-sdk-v2.2-lnx32/lib/x86/ -lOpenCL
```
The LD_LIBRARY_PATH is needed for running an OpenCL program.

---

### Post by slow photon on 2010-08-20
Thank you very much for the help kutya61! I appreciate the help

---

### Post by t2kburl on 2010-12-01
I'm trying to get this going on Maverick. I think I did everything right but when I run make I get this:

```
In file included from BoxFilterGLSAT.hpp:105,
                 from BoxFilterGL.cpp:93:
../../../../../include/GL/glew.h:1138: fatal error: GL/glu.h: No such file or directory
compilation terminated.
```


Help!

---

### Post by kutya61 on 2010-12-30
Hi!
You should install libglew1.5-dev and libglu1-mesa-dev packages. The former will give you /usr/include/GL/glew.h, and the latter will give /usr/include/GL/glu.h .
The command:
```
sudo apt-get install libglew1.5-dev libglu1-mesa-dev
```

I think you have libglew1.5-dev already, only the other is missing. These libraries are not related to Open**CL**, but Open**GL**.

---

### Post by obinine on 2011-01-06
You can download Ubuntu ATI OpenCL packages now from
[http://forums.amd.com/forum/messageview.cfm?catid=390&threadid=125792&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear](http://forums.amd.com/forum/messageview.cfm?catid=390&threadid=125792&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear)

---

### Post by t2kburl on 2011-04-10
Has anyone tried enabling OpenCL Link in Mathematica 8?

I have been able to build and run the sample apps that come with the stream SDK pack, but no luck with Mathematica. :confused:

---

### Post by Claus7 on 2011-04-12
Hello,

trying to compile another program with opencl I came across your post.

For mathematica I saw that openCLLink should do the job on what you are asking. Since your sdk installation went ok, as long as you are able to run the examples, then have you tried to do from mathematica the following:
[http://reference.wolfram.com/mathematica/OpenCLLink/tutorial/Setup.html#509267359](http://reference.wolfram.com/mathematica/OpenCLLink/tutorial/Setup.html#509267359)

what are the output you get from there commands?

If you have informed your .bashrc correctly about opencl libraries these should not post errors, as mathematica does not require a special installation procedure in order to use opencl libraries.

Regards!

---

### Post by Ezzedine on 2011-04-13
Hello all, 


I try to use openCL with Nvidia Quardo FX 1700. I install gpucomputingSDK , cudatoolkit and the driever card. Baut when i compile the source. i have an error : cl_platform.h file not found.
But it's in the same folder than cl.h. 

Any idea please ?

---

### Post by RedRoss on 2011-04-13
Really liked the guide of how to setup amd_app here. But it seems I have a problem with my version of catalyst (?). Any ideas ho w to fix:
*** CAL version mismatch:
This OpenCL build requires version 1.4.879, version 1.4.838 installed.

---

### Post by codedivine on 2011-04-13
> **RedRoss said:**
> Really liked the guide of how to setup amd_app here. But it seems I have a problem with my version of catalyst (?). Any ideas ho w to fix:
*** CAL version mismatch:
This OpenCL build requires version 1.4.879, version 1.4.838 installed.

You are running an old version of the graphics driver. Install the latest version from AMD's website.

---

### Post by t2kburl on 2011-04-16
> **Claus7 said:**
> Hello,

trying to compile another program with opencl I came across your post.

For mathematica I saw that openCLLink should do the job on what you are asking. Since your sdk installation went ok, as long as you are able to run the examples, then have you tried to do from mathematica the following:
[http://reference.wolfram.com/mathematica/OpenCLLink/tutorial/Setup.html#509267359](http://reference.wolfram.com/mathematica/OpenCLLink/tutorial/Setup.html#509267359)

what are the output you get from there commands?

If you have informed your .bashrc correctly about opencl libraries these should not post errors, as mathematica does not require a special installation procedure in order to use opencl libraries.

Regards!
I have followed the mathematica tutorial, but when I run OpenCLQ[] it always returns *False*

I'll have to check my .bashrc. I will post the relevant lines here as an edit when I can. Maybe I screwed it up ...???? But I would think that would cause problems with the samples, too.Here are the lines I entered in my .bashrc

> export ATISTREAMSDKROOT=/home/t2kburl/Downloads/ati-stream-sdk-v2.3-lnx64/
export ATISTREAMSDKSAMPLESROOT=/home/t2kburl/Downloads/ati-stream-sdk-v2.3-lnx64/samples/opencl/bin/x86_64/
export LD_LIBRARY_PATH=$ATISTREAMSDKROOT/lib/x86_64:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=$ATISTREAMSDKROOT/lib/x86:$ATISTREAMSDKROOT/lib/x86_64:$LD_LIBRARY_PATH

---

### Post by Claus7 on 2011-04-18
Hello,

> **t2kburl said:**
> I have followed the mathematica tutorial, but when I run OpenCLQ[] it always returns *False*

I'll have to check my .bashrc. I will post the relevant lines here as an edit when I can. Maybe I screwed it up ...???? But I would think that would cause problems with the samples, too.Here are the lines I entered in my .bashrc

trying to get the gist of it lately, I should say that you might have messed up your .bashrc

Instead of typing this, in a 64 bit machine I would go for something like:

> export LD_LIBRARY_PATH=$LD_LIBRARY_PATH":/*path*/AMD-APP-SDK-v2.4-lnx64/lib/x86_64/"
export LIBRARY_PATH=$LIBRARY_PATH":/*path*/AMD-APP-SDK-v2.4-lnx64/lib/x86_64/"
export C_INCLUDE_PATH=$C_INCLUDE_PATH":/*path*/AMD-APP-SDK-v2.4-lnx64/include/"

I think that you have double exported LD_LIBRARY_PATH.

Regards!

---

### Post by t2kburl on 2011-04-18
Well .... I made the corrections you suggested, as well as updating to AMD APP 2.4, (which I'm not sure Mathematica could find, since it is checking for ATISTREAMSDKROOT). I followed the Mathematica tutorial and OpenCLQ still returns False

I ran this in a terminal to see if the path was correct, and it is.

```
 echo $ATISTREAMSDKROOT
/home/t2kburl/Downloads/ati-stream-sdk-v2.3-lnx64/lib/x86_64/
```

I have the latest fglrx installed. I have a 5770, so thats not the problem.

Any ideas? :confused:

---

### Post by abduld on 2011-04-19
this is due to AMD renaming the library after the Mathematica release. Can you try doing 

cd AMD-APP-SDK-v2.4-lnx64/lib/x86_64
cp libamdocl64.so libatiocl64.so

you also need to install the icd-registration.tgz file, this is done by doing

cd /
tar -xf /path/to/AMD-APP-SDK-v2.4-lnx64/icd-registration.tgz

---

### Post by Claus7 on 2011-04-19
Hello,

> **t2kburl said:**
> Well .... I made the corrections you suggested, as well as updating to AMD APP 2.**4**, (which I'm not sure Mathematica could find, since it is checking for ATISTREAMSDKROOT). I followed the Mathematica tutorial and OpenCLQ still returns False

I ran this in a terminal to see if the path was correct, and it is.

```
 echo $ATISTREAMSDKROOT
/home/t2kburl/Downloads/ati-stream-sdk-v2.**3**-lnx64/lib/x86_64/
```

I have the latest fglrx installed. I have a 5770, so thats not the problem.

Any ideas? :confused:

how is it possible that you have updated the version of app, while the result is giving you the version 2.3?

I would also do what *abduld* proposed. Since I'm not on my pc right now, I should advice you to do that as root, since the license is installed under /etc directory, if I recall correctly.

Regards!

---

### Post by t2kburl on 2011-04-19
The new version is $AMDAPPSDKROOT
According to the Mathematica tutorial, OpenCLQ[] is checking $ATISTREAMSDKROOT

For what its worth, I'm using the install guide provided by AMD
I did the icd registration part.

Thanks for the help. I really want to get this working.

But, it is still not

---

### Post by abduld on 2011-04-19
you have to use $ATISTREAMSDKROOT to get OpenCLLink working, since that is what it checks.

You might want to post the output of

OpenCLInformation[]

this will actually give an error that should give you an idea where things are failing. And, if you are using Mathematica 8.0.1 (I suggest that you update if you are not using it), then you can do


Exit (* make sure you are in a fresh kernel *)
<<OpenCLLink`
GPUTools`Utilities`VerboseLogPrinter = Print;
OpenCLInformation[]

---

### Post by t2kburl on 2011-04-19
```
In[1]:= Needs["OpenCLLink`"]

In[2]:= OpenCLQ[]

Out[2]= False

In[9]:= Exit

In[1]:= << OpenCLLink`
GPUTools`Utilities`VerboseLogPrinter = Print;
OpenCLInformation[]

During evaluation of In[1]:= OpenCLInformation::syslibfld: OpenCL failed to load system libraries. Refer to OpenCLLink System Requirements for system requirements. >>

Out[3]= OpenCLInformation[]
```

Hmm ... failed to load system libraries ...???

I am still using 8.0. I have not upgraded to 8.0.1 yet.

---

### Post by abduld on 2011-04-19
it might be best to upgrade. You'd get other fixes in the process.

---

### Post by t2kburl on 2011-04-19
Not an option. I'm running a under a site license via my university. I can't update until they do.

---

### Post by Claus7 on 2011-04-22
Hello,

since you seem to have opencl installation problems, you might want to check out **noo**'s deb packages from amd's forums.

Since is not straightforward on how to get there, here:
[http://ubuntuforums.org/showpost.php?p=10706214&postcount=15](http://ubuntuforums.org/showpost.php?p=10706214&postcount=15)
in step:
Download and install the ATI GPU Computing SDK

you will get a notion on what to do.

Up to now, the tests I have made, are ok. If something goes wrong, you can remove the deb files from your ubu box pretty easily. Just to add, that while doing so, do not forget to comment out (by putting # in front of the lines) the export commands you had in your .bashrc file.

Regards!

---

### Post by t2kburl on 2011-04-24
It appears Mathematica (for some reason) doesn't support my GPU, even though its on their list of supported hardware.
I can use opencl for my own programs, but I can not use it with Mathematica.

I think I'm going back to NVIDIA for my next GPU

---

### Post by Claus7 on 2011-04-24
Hello,

you may drop them a line (the mathematica people) and check out their opinion about your card. They might give you some more info that will make your life easier.

Hope the best,
Regards!

---

### Post by t2kburl on 2011-05-02
Since upgrading to natty required a clean install due to post boot hanging, I am starting over from scratch on this. 
However, I'm not encouraged by the fact that I tried to get this done in Win7 with Mathematica 8.0.1 installed and it failed, too :(

ugh! ati driver won't even install now :(

> Option: 'Build package for detected OS: Ubuntu/natty' ? [N/y] y
Installing to /
1061 MB available, 1 MB will be installed.

Continue install? [Y/n] y
 Generating package Ubuntu/natty
Installing Build package for detected OS: Ubuntu/natty ...
 100% - //usr/share/ati//ATI_LICENSE.TXT
 100% - //usr/share/ati/ATI_LICENSE.TXT

Installation complete.
*** glibc detected *** ./setup.data/bin/x86_64/setup: double free or corruption (fasttop): 0x0000000001765020 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a8f)[0x7f315ce2fa8f]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x73)[0x7f315ce338e3]
./setup.data/bin/x86_64/setup[0x40a6b5]
./setup.data/bin/x86_64/setup[0x4128fb]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xff)[0x7f315cdd5eff]
./setup.data/bin/x86_64/setup[0x40382a]


---

### Post by Claus7 on 2011-05-04
Hello,

humble reply would be that this was not a problem from maverick. 

You could wait a little and install catalyst 11.4 which supports your card (hd 5770 that is) and would be the latest in the series. Also you were able to run also some programs with opencl, which lessens the fact that maverick fails you...

Anyway, since you started from scratch, I would recommend you to check out this guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

This might help you on the installation of the driver.

Good luck,
Regards!

---

### Post by t2kburl on 2011-05-04
I was able to get mathematica opencl link working in Win7 (thanks abduld), and I have the 11.4 ati driver installed in Natty now.

But now the mathematica installer errors out in Natty. (something about a print fail) So the frustration continues. ](*,)

CRITICAL FAILURE: PrintIntroduction() Error
  $ProductTitle not defined.
 
?????

---

### Post by qodsec on 2011-05-06
you should really be talking to tech support at Wolfram, but I think the solution is to move the installer shell script to your /tmp directory and run it from there.

---

### Post by jaidotsh on 2011-05-28
Hello, I followed all steps to install OpenCL on my Ubuntu 11.04(on ATI 4300series, Intel corei3). But I get this error every time I run a sample

./BlackScholes: error while loading shared libraries: libOpenCL.so.1: cannot open shared object file: No such file or directory

I did export the environment variable(a 100 times), but I still get this error. Help!

---

### Post by Claus7 on 2011-06-01
Hello,

I do not know what blackscholes is or how you did the compilation, yet it seems that something is missing. In case you gave some more info about the program and the steps you took to install the libraries might have shed more light to the problem.

Now, no experience on natty. Maybe my guide on maverick will help you make available the libraries you want:
[http://ubuntuforums.org/showpost.php?p=10706214&postcount=15](http://ubuntuforums.org/showpost.php?p=10706214&postcount=15)

Oh! And welcome to the forums!

Hope this helps,
Regards!

---

