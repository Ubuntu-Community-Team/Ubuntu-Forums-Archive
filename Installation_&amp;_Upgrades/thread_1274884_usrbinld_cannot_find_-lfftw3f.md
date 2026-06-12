---
title: "/usr/bin/ld: cannot find -lfftw3f"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by tvkpz on 2009-09-25
Hi 

I installed fftw3 using simple ./configure, make and make install commands as directed by fftw. But when I try compile a simple program that uses fftw3 I get an error.

Here is the compilation code and following that is the error report. I checked all the fftw3 related libs are either in /usr/local/lib or /usr/lib so I added both.

Appreciate any help. Thanks!

gcc -Wall -g -o compute_gist compute_gist.c gist.o standalone_image.o -L/usr/lib -L/usr/local/lib -lfftw3f
/usr/bin/ld: cannot find -lfftw3f
collect2: ld returned 1 exit status
make: *** [compute_gist] Error 1

---

### Post by lloyd_b on 2009-09-25
> **tvkpz said:**
> Hi 

I installed fftw3 using simple ./configure, make and make install commands as directed by fftw. But when I try compile a simple program that uses fftw3 I get an error.

Here is the compilation code and following that is the error report. I checked all the fftw3 related libs are either in /usr/local/lib or /usr/lib so I added both.

Appreciate any help. Thanks!

gcc -Wall -g -o compute_gist compute_gist.c gist.o standalone_image.o -L/usr/lib -L/usr/local/lib -lfftw3f
/usr/bin/ld: cannot find -lfftw3f
collect2: ld returned 1 exit status
make: *** [compute_gist] Error 1

Try running "sudo ldconfig" - it may be that the system just hasn't added the libraries into ld's cache as yet.

Lloyd B.

---

### Post by tvkpz on 2009-09-27
Hi Lloyd,

Thank for your reply.

I tried doing sudo ldconfig. But I still get the same error message.

gcc -Wall -g -o compute_gist compute_gist.c gist.o standalone_image.o -L/usr/lib -L/usr/local/lib -lfftw3f
/usr/bin/ld: cannot find -lfftw3f
collect2: ld returned 1 exit status
make: *** [compute_gist] Error 1

I checked using sudo ldconfig -p and saw that the following is in there

    libfftw3l_threads.so.3 (libc6) => /usr/lib/libfftw3l_threads.so.3
    libfftw3l.so.3 (libc6) => /usr/lib/libfftw3l.so.3
    libfftw3f_threads.so.3 (libc6) => /usr/lib/libfftw3f_threads.so.3
    libfftw3f.so.3 (libc6) => /usr/lib/libfftw3f.so.3
    libfftw3_threads.so.3 (libc6) => /usr/lib/libfftw3_threads.so.3
    libfftw3.so.3 (libc6) => /usr/lib/libfftw3.so.3

Not sure why I get this error. Appreciate your help with this.

---

### Post by tvkpz on 2009-09-28
Hi

The problem got solved.

I had not installed fftw3-dev although I had installed fftw3.

Just did

sudo apt-get install fftw3-dev

and viola! It worked.

Thanks

---

