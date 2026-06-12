---
title: "changing shared libaries"
date: 2008-09-17
forum: General Help
---

### Post by pjkoczan on 2008-09-17
I was wondering if anyone knew of a way to change which shared libraries are loaded when running a particular binary, but without having to set LD_LIBRARY_PATH, which I'd prefer to not do.

It's not going to be as clean and easy as recompiling since this was a binary-only distribution (Oracle client, for those who are interested).

Basically, I'd like to go from this...

```

$ ldd /opt/oracle/bin/sqlplus 
        linux-gate.so.1 =>  (0x00ccc000)
        libsqlplus.so => not found
        libclntsh.so.11.1 => not found
        libnnz11.so => not found
        libdl.so.2 => /lib/libdl.so.2 (0x00830000)
        libm.so.6 => /lib/libm.so.6 (0x00807000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00836000)
        libnsl.so.1 => /lib/libnsl.so.1 (0x00702000)
        libc.so.6 => /lib/libc.so.6 (0x008fa000)
        /lib/ld-linux.so.2 (0x007e5000)

```

...to this...

```

$ ldd /opt/oracle/bin/sqlplus 
        linux-gate.so.1 =>  (0x003a6000)
        libsqlplus.so => /opt/oracle/lib/libsqlplus.so (0x00cae000)
        libclntsh.so.11.1 => /opt/oracle/lib/libclntsh.so.11.1 (0x00d54000)
        libnnz11.so => /opt/oracle/lib/libnnz11.so (0x00110000)
        libdl.so.2 => /lib/libdl.so.2 (0x00be1000)
        libm.so.6 => /lib/libm.so.6 (0x00bb8000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00be7000)
        libnsl.so.1 => /lib/libnsl.so.1 (0x0096d000)
        libc.so.6 => /lib/libc.so.6 (0x00a73000)
        libaio.so.1 => /usr/lib/libaio.so.1 (0x006ec000)
        /lib/ld-linux.so.2 (0x00a55000)

```

Is there any way to do this without setting LD_LIBRARY_PATH (i.e. safely editing the binary)?

---

### Post by unutbu on 2008-09-17
```
sudo ldconfig -n /opt/oracle/lib
```
See [http://www.linux.com/feature/114007](http://www.linux.com/feature/114007)

---

### Post by pjkoczan on 2008-09-17
> **unutbu said:**
> ```
sudo ldconfig -n /opt/oracle/lib
```
See [http://www.linux.com/feature/114007](http://www.linux.com/feature/114007)

I might have to get a little creative as to how to deploy this to all the systems that need it, but more or less that's exactly what I was looking for. Thanks.

---

