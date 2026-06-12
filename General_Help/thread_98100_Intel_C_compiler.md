---
title: "Intel C compiler"
date: 2005-12-02
forum: General Help
---

### Post by WebDrake on 2005-12-02
Hello all,

I've been trying to install the Intel C compiler on my system.  Everything seems to be in place except for one thing: the shell commands provided to set the path variables don't work, producing simply a message, "What manual page do you want?"

Here are the two shell commands:

```

#! /bin/sh

if [ -z "${PATH}" ]
then
    PATH="/opt/intel/cc/9.0/bin"; export PATH
else
    PATH="/opt/intel/cc/9.0/bin:$PATH"; export PATH
fi

if [ -z "${LD_LIBRARY_PATH}" ]
then
    LD_LIBRARY_PATH="/opt/intel/cc/9.0/lib"; export LD_LIBRARY_PATH
else
    LD_LIBRARY_PATH="/opt/intel/cc/9.0/lib:$LD_LIBRARY_PATH"; export LD_LIBRARY_PATH
fi

if [ -z "${MANPATH}" ]
then
    MANPATH="/opt/intel/cc/9.0/man":$(man -w); export MANPATH
else
    MANPATH="/opt/intel/cc/9.0/man:${MANPATH}"; export MANPATH
fi


if [ -z "${INTEL_LICENSE_FILE}" ]
then
        INTEL_LICENSE_FILE="/opt/intel/cc/9.0/licenses:/opt/intel/licenses:${HOME}/intel/licenses"; export INTEL_LICENSE_FILE
else
        INTEL_LICENSE_FILE="${INTEL_LICENSE_FILE}:/opt/intel/cc/9.0/licenses:/opt/intel/licenses:${HOME}/intel/licenses"; export INTEL_LICENSE_FILE
fi

```

and

```

#! /bin/sh

if [ -z "${PATH}" ]
then
    PATH="/opt/intel/idb/9.0/bin"; export PATH
else
    PATH="/opt/intel/idb/9.0/bin:$PATH"; export PATH
fi

if [ -z "${MANPATH}" ]
then
    MANPATH="/opt/intel/idb/9.0/man":$(man -w); export MANPATH
else
    MANPATH="/opt/intel/idb/9.0/man:${MANPATH}"; export MANPATH
fi

```

and their .csh equivalents:

```

#! /bin/tcsh

if !($?PATH) then
    setenv PATH /opt/intel/cc/9.0/bin
else
    setenv PATH /opt/intel/cc/9.0/bin:$PATH
endif

if !($?LD_LIBRARY_PATH) then
    setenv LD_LIBRARY_PATH /opt/intel/cc/9.0/lib
else
    setenv LD_LIBRARY_PATH /opt/intel/cc/9.0/lib:$LD_LIBRARY_PATH
endif

if !($?MANPATH) then
    setenv MANPATH /opt/intel/cc/9.0/man:`man -w`
else
    setenv MANPATH /opt/intel/cc/9.0/man:$MANPATH
endif

if !($?INTEL_LICENSE_FILE) then
    setenv INTEL_LICENSE_FILE /opt/intel/cc/9.0/licenses:/opt/intel/licenses:$HOME/intel/licenses
else
    setenv INTEL_LICENSE_FILE /opt/intel/cc/9.0/licenses:/opt/intel/licenses:$HOME/intel/licenses:$INTEL_LICENSE_FILE
endif

```

and

```

#! /bin/tcsh

if !($?PATH) then
    setenv PATH /opt/intel/idb/9.0/bin
else
    setenv PATH /opt/intel/idb/9.0/bin:$PATH
endif

if !($?MANPATH) then
    setenv MANPATH /opt/intel/idb/9.0/man:`man -w`
else
    setenv MANPATH /opt/intel/idb/9.0/man:$MANPATH
endif

```

Any ideas what's wrong?

Many thanks,

         -- Joe

---

### Post by cylon359 on 2005-12-02
Yeah, the "man -w" part is messing it up.  Can you edit the scripts and remove the calls to that?

---

