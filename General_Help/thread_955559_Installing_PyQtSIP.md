---
title: "Installing PyQt/SIP"
date: 2008-10-22
forum: General Help
---

### Post by BetaMaster on 2008-10-22
[b]UPDATE:
I wasn't able to get SIP to make correctly, but I found that all I had to do was install python-qt3 in Synaptic (I had previously installed qt4 to no avail).[/b]

I've recently reinstalled Ubuntu, and am now trying to install PyQt, and ran into the dependency issue that it requires SIP. I try installing SIP, and it won't work.
When I run 'python configure.py' it configures fine, but after running 'make' I get, well..

```
siplib.c: In function ‘sipWrapper_dealloc’:
siplib.c:7460: error: ‘PyObject’ undeclared (first use in this function)
siplib.c:7460: error: expected expression before ‘)’ token
siplib.c:7477: error: ‘sipTypeDef’ has no member named ‘td_dealloc’
siplib.c:7478: error: ‘sipTypeDef’ has no member named ‘td_dealloc’
siplib.c:7488: error: ‘sipWrapper’ has no member named ‘pySigList’
siplib.c:7494: error: ‘sipWrapper’ has no member named ‘pySigList’
siplib.c:7495: error: ‘sipWrapper’ has no member named ‘pySigList’
siplib.c:7508: error: ‘PyBaseObject_Type’ undeclared (first use in this function)
siplib.c:7508: error: expected expression before ‘)’ token
siplib.c: At top level:
siplib.c:7515: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:7528: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:7553: error: expected ‘)’ before ‘*’ token
siplib.c:7563: error: expected ‘)’ before ‘*’ token
siplib.c:7572: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:7619: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:7669: error: expected declaration specifiers or ‘...’ before ‘PyObject’
siplib.c: In function ‘getNonStaticVariables’:
siplib.c:7671: error: ‘PyMethodDef’ undeclared (first use in this function)
siplib.c:7671: error: ‘pmd’ undeclared (first use in this function)
siplib.c:7673: error: ‘sipWrapperType’ has no member named ‘type’
siplib.c:7676: error: ‘METH_STATIC’ undeclared (first use in this function)
siplib.c:7679: error: ‘PyObject’ undeclared (first use in this function)
siplib.c:7679: error: ‘val’ undeclared (first use in this function)
siplib.c:7679: error: ‘dict’ undeclared (first use in this function)
siplib.c:7685: error: ‘ndict’ undeclared (first use in this function)
siplib.c:7687: error: ‘sipWrapper’ has no member named ‘dict’
siplib.c:7693: error: expected expression before ‘)’ token
siplib.c: At top level:
siplib.c:7714: error: expected ‘)’ before ‘*’ token
siplib.c:7736: error: extra brace group at end of initializer
siplib.c:7736: error: (near initialization for ‘sipWrapper_Type’)
siplib.c:7738: error: extra brace group at end of initializer
siplib.c:7738: error: (near initialization for ‘sipWrapper_Type’)
siplib.c:7739: error: ‘sipWrapperType_Type’ undeclared here (not in a function)
siplib.c:7740: error: expected ‘}’ before numeric constant
siplib.c: In function ‘addSlots’:
siplib.c:7796: error: ‘sipTypeDef’ has no member named ‘td_readbuffer’
siplib.c:7800: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:7800: error: ‘getreadbufferproc’ undeclared (first use in this function)
siplib.c:7800: error: expected ‘;’ before ‘sipWrapper_getreadbuffer’
siplib.c:7803: error: ‘sipTypeDef’ has no member named ‘td_writebuffer’
siplib.c:7807: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:7807: error: ‘getwritebufferproc’ undeclared (first use in this function)
siplib.c:7807: error: expected ‘;’ before ‘sipWrapper_getwritebuffer’
siplib.c:7810: error: ‘sipTypeDef’ has no member named ‘td_segcount’
siplib.c:7814: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:7814: error: ‘getsegcountproc’ undeclared (first use in this function)
siplib.c:7814: error: expected ‘;’ before ‘sipWrapper_getsegcount’
siplib.c:7817: error: ‘sipTypeDef’ has no member named ‘td_charbuffer’
siplib.c:7821: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:7821: error: ‘getcharbufferproc’ undeclared (first use in this function)
siplib.c:7821: error: expected ‘;’ before ‘sipWrapper_getcharbuffer’
siplib.c:7826: error: ‘PyTypeObject’ undeclared (first use in this function)
siplib.c:7826: error: expected expression before ‘)’ token
siplib.c:7831: error: ‘sipWrapperType’ has no member named ‘type’
siplib.c: At top level:
siplib.c:7840: error: expected ‘)’ before ‘*’ token
siplib.c: In function ‘findClass’:
siplib.c:8146: error: ‘sipExportedModuleDef’ has no member named ‘em_types’
siplib.c:8148: error: ‘sipExportedModuleDef’ has no member named ‘em_nrtypes’
siplib.c:8155: error: ‘sipWrapperType’ has no member named ‘type’
siplib.c:8157: error: ‘sipWrapperType’ has no member named ‘type’
siplib.c:8160: error: ‘sipWrapperType’ has no member named ‘type’
siplib.c: At top level:
siplib.c:8227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c: In function ‘findEnumArg’:
siplib.c:8257: error: ‘PyTypeObject’ undeclared (first use in this function)
siplib.c:8257: error: ‘py’ undeclared (first use in this function)
siplib.c:8267: error: ‘union <anonymous>’ has no member named ‘et’
siplib.c: In function ‘sipFindSigArgType’:
siplib.c:8289: error: ‘sipExportedModuleDef’ has no member named ‘em_typedefs’
siplib.c:8324: error: ‘sipExportedModuleDef’ has no member named ‘em_mappedtypes’
siplib.c:8340: error: ‘sipExportedModuleDef’ has no member named ‘em_types’
siplib.c:8344: error: ‘sipExportedModuleDef’ has no member named ‘em_mappedtypes’
siplib.c:8344: error: ‘sipExportedModuleDef’ has no member named ‘em_mappedtypes’
siplib.c:8348: error: ‘sipExportedModuleDef’ has no member named ‘em_enums’
siplib.c:8353: error: ‘sipPyObject’ has no member named ‘next’
siplib.c:8357: error: ‘sipPyObject’ has no member named ‘object’
siplib.c:8359: error: ‘sipPyObject’ has no member named ‘object’
siplib.c: At top level:
siplib.c:8420: error: expected ‘)’ before ‘*’ token
siplib.c: In function ‘qt_and_sip_api_3_4’:
siplib.c:8506: error: ‘sipWrapperType’ has no member named ‘type’
siplib.c: At top level:
siplib.c:8513: error: expected declaration specifiers or ‘...’ before ‘visitproc’
siplib.c: In function ‘visitSlot’:
siplib.c:8516: error: ‘sipSlot’ has no member named ‘weakSlot’
siplib.c:8516: error: ‘Py_True’ undeclared (first use in this function)
siplib.c:8516: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c:8516: error: ‘Py_None’ undeclared (first use in this function)
siplib.c:8517: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c: In function ‘clearAnySlotReference’:
siplib.c:8528: error: ‘sipSlot’ has no member named ‘weakSlot’
siplib.c:8528: error: ‘Py_True’ undeclared (first use in this function)
siplib.c:8530: error: ‘PyObject’ undeclared (first use in this function)
siplib.c:8530: error: ‘xref’ undeclared (first use in this function)
siplib.c:8530: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c:8536: error: ‘Py_None’ undeclared (first use in this function)
siplib.c:8537: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c: At top level:
siplib.c:8547: error: expected ‘)’ before ‘*’ token
siplib.c:8565: error: expected ‘)’ before ‘*’ token
siplib.c:8587: error: expected ‘)’ before ‘*’ token
siplib.c:8612: error: expected ‘)’ before ‘*’ token
siplib.c:8748: error: expected ‘)’ before ‘*’ token
siplib.c:8759: error: expected ‘)’ before ‘*’ token
siplib.c: In function ‘raiseNoWChar’:
siplib.c:8772: error: ‘PyExc_SystemError’ undeclared (first use in this function)
make[1]: *** [siplib.o] Error 1
make[1]: Leaving directory `/home/brad/Desktop/sip-4.7.7/siplib'
make: *** [all] Error 2
brad@brad-desktop:~/Desktop/sip-4.7.7$ 
```

That's only a small fraction of the last portion, because it's more than 2000 lines. Basically, *every* aspect of the code is failing. Am I missing another dependency? I have gcc and gpp installed, if that would matter at all. I'm not sure what to do though. Any help?

---

### Post by rhondodedron on 2009-02-06
Hi

i'm facing the exact same problem

I'm using Debian etch

How do i solve it ?

---

### Post by snova on 2009-02-06
> **rhondodedron said:**
> Hi

i'm facing the exact same problem

I'm using Debian etch

How do i solve it ?

Install either python-qt3 or python-qt4, depending on which version you need.

No need to compile from source...

---

### Post by nlu on 2009-05-01
Hi
Install python dev (for example python2.6-dev) to make sip
Goodluck

---

### Post by ender0887 on 2009-07-09
I am having this same problem.
In order to install pyqt3, you need to have sip already installed. But my sip install isn't working (same error as above).
I cannot seem to fix the problem. Any ideas?

---

### Post by lhrt on 2009-07-24
Try install the python-devel package

---

