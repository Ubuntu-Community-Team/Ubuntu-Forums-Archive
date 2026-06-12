---
title: "[SOLVED] shared library dependencies error...ldconfig experts?"
date: 2008-09-09
forum: General Help
---

### Post by mitch_feaster on 2008-09-09
So after installing the xilinx ise webpack ldconfig is pointing to the wrong libstdc++.so.6 shared library.  This is giving me errors when I try to run programs that need this shared library.  For example, I get:

```

mgalgs@sonlinha:~$ octave
octave: /home/mgalgs/ISE/lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/octave-3.0.0/liboctinterp.so)
octave: /home/mgalgs/ISE/lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/octave-3.0.0/liboctave.so)

```

and

```

mgalgs@sonlinha:~$ apt-cache search fortran
apt-cache: /home/mgalgs/ISE/lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-cache)
apt-cache: /home/mgalgs/ISE/lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)

```

Also here are some files you'll probably want to know about:

```

mgalgs@sonlinha:~$ cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf

```

and

```

 cat /etc/ld.so.conf.d/*
# Multiarch support
/lib/i486-linux-gnu
/usr/lib/i486-linux-gnu
# libc default configuration
/usr/local/lib

```


and those are just the first two I've found...I don't know if ise messed any other shared objects up (I assume it did because it came with a whole bunch).  Anyways, does anyone know how to get ldconfig to point back to /usr/lib/libstdc++.so.6?



this might be of some help:

```

mgalgs@sonlinha:~$ ldd `which octave`
/usr/bin/octave: /home/mgalgs/ISE/lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/octave-3.0.0/liboctinterp.so)
/usr/bin/octave: /home/mgalgs/ISE/lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/octave-3.0.0/liboctave.so)
	linux-gate.so.1 =>  (0xb7f70000)
	liboctinterp.so => /usr/lib/octave-3.0.0/liboctinterp.so (0xb755d000)
	liboctave.so => /usr/lib/octave-3.0.0/liboctave.so (0xb6cd1000)
	libcruft.so => /usr/lib/octave-3.0.0/libcruft.so (0xb6c7e000)
	libumfpack.so.3.1.0 => /usr/lib/libumfpack.so.3.1.0 (0xb6bc6000)
	libamd.so.3.1.0 => /usr/lib/libamd.so.3.1.0 (0xb6bbe000)
	libcamd.so.3.1.0 => /usr/lib/libcamd.so.3.1.0 (0xb6bb5000)
	libcolamd.so.3.1.0 => /usr/lib/libcolamd.so.3.1.0 (0xb6bac000)
	libcholmod.so.3.1.0 => /usr/lib/libcholmod.so.3.1.0 (0xb6ae1000)
	libccolamd.so.3.1.0 => /usr/lib/libccolamd.so.3.1.0 (0xb6ad6000)
	libcxsparse.so.3.1.0 => /usr/lib/libcxsparse.so.3.1.0 (0xb6aab000)
	liblapack.so.3gf => /usr/lib/liblapack.so.3gf (0xb63b9000)
	libblas.so.3gf => /usr/lib/libblas.so.3gf (0xb633b000)
	libfftw3.so.3 => /usr/lib/libfftw3.so.3 (0xb6254000)
	libreadline.so.5 => /lib/libreadline.so.5 (0xb6223000)
	libncurses.so.5 => /lib/libncurses.so.5 (0xb61f3000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb61ef000)
	libhdf5-1.6.5.so.0 => /usr/lib/libhdf5-1.6.5.so.0 (0xb60c8000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb60b3000)
	libgfortran.so.2 => /usr/lib/libgfortran.so.2 (0xb601b000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb5ff6000)
[COLOR="Red"]	libstdc++.so.6 => /home/mgalgs/ISE/lib/lin/libstdc++.so.6 [/COLOR](0xb5f16000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb5f0b000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb5dbc000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb5da3000)
	/lib/ld-linux.so.2 (0xb7f71000)


```


Thanks for the help in advance!

---

### Post by cdtech on 2008-09-09
Some information I found about the libstdc++.so.6 that may help:
[http://www.nabble.com/%60GLIBCXX_3.4.9%27-not-found-td18389950.html](http://www.nabble.com/%60GLIBCXX_3.4.9%27-not-found-td18389950.html)

---

### Post by mitch_feaster on 2008-09-09
Hmmm, the problem is that I didn't compile anything.  It's almost as if the xilinx installer made ldconfig look at the libstdc++.so.6 in my home directory rather than the regular one.  I just need to figure out how to direct it back...

---

### Post by mitch_feaster on 2008-09-09
Okay I figured it out and I feel quite silly about what the problem was!  If anyone has the same problem here's what I did.
My problem was that I was source'ing a file in my .bashrc that was modifying the LD_LIBRARY_PATH and it wasn't looking in /usr/lib anymore.  So I just did a good old
```

export LD_LIBRARY_PATH=/usr/lib/:${LD_LIBRARY_PATH}

```
and everything was back to normal!

---

