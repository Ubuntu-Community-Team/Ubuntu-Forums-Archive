---
title: "Problems installing software - python related"
date: 2008-08-27
forum: General Help
---

### Post by laurence91 on 2008-08-27
Hi, iv been using Kubuntu for a little while now and am fine with day to day stuff, however i have been trying to install some software (for work) and i keep hitting a dead end.
its an NMR programme, i doubt many people will be familliar called ccpn. I had to download and install some packages as part of the install ...

    * Python - python2.4.tar.gz
    * Tcl/Tk - tcltk8.4.tar.gz
    * Mesa - mesa6.0.tar.gz

Which i thought went ok, until the very last step when it puts this out in the terminal ...

In file included from python_util.c:48:
python_util.h:51:20: error: Python.h: No such file or directory
In file included from python_util.c:48:
python_util.h:74: error: expected ‘)’ before ‘*’ token
python_util.h:77: error: expected ‘)’ before ‘*’ token
python_util.h:80: error: expected ‘)’ before ‘*’ token
python_util.h:83: error: expected ‘)’ before ‘*’ token
python_util.h:86: error: expected ‘)’ before ‘*’ token
python_util.h:89: error: expected ‘)’ before ‘*’ token
python_util.h:92: error: expected ‘)’ before ‘*’ token
python_util.h:95: error: expected ‘)’ before ‘*’ token
python_util.h:98: error: expected ‘)’ before ‘*’ token
python_util.h:101: error: expected ‘)’ before ‘*’ token
python_util.h:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.h:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.h:109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.h:112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.h:116: error: expected ‘)’ before ‘*’ token
python_util.h:119: error: expected ‘)’ before ‘*’ token
python_util.c:52: error: expected ‘)’ before ‘*’ token
python_util.c:57: error: expected ‘)’ before ‘*’ token
python_util.c:71: error: expected ‘)’ before ‘*’ token
python_util.c:123: error: expected ‘)’ before ‘*’ token
python_util.c:181: error: expected ‘)’ before ‘*’ token
python_util.c:236: error: expected ‘)’ before ‘*’ token
python_util.c:297: error: expected ‘)’ before ‘*’ token
python_util.c:359: error: expected ‘)’ before ‘*’ token
python_util.c:414: error: expected ‘)’ before ‘*’ token
python_util.c:475: error: expected ‘)’ before ‘*’ token
python_util.c:537: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.c:556: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.c:575: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.c:595: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
python_util.c:623: error: expected ‘)’ before ‘*’ token
python_util.c:652: error: expected ‘)’ before ‘*’ token
make[1]: *** [python_util.o] Error 1
make[1]: Leaving directory `/home/laurence/Documents/CCPNMR/ccpnmr/ccpnmr1.0/c/memops/global'
make: *** [global] Error 2
Do you want to create a bin directory (answer y unless you know otherwise) (y or n)? y
Creating the bin directory
Could not remove directory ccpnmr1.0/data/ccp/chemComp/nonpolymer (probably not a problem)
Run Analysis (as test) (y or n)? y
Error, the Analysis module will not work, something is wrong with the C code.
Traceback (most recent call last):
  File "/home/laurence/Documents/CCPNMR/ccpnmr/ccpnmr1.0/python/ccpnmr/analysis/AnalysisGui.py", line 72, in <module>
    from ccpnmr.analysis.AnalysisPopup import AnalysisPopup
  File "/home/laurence/Documents/CCPNMR/ccpnmr/ccpnmr1.0/python/ccpnmr/analysis/AnalysisPopup.py", line 92, in <module>
    from ccpnmr.analysis.Analysis                      import Analysis
  File "/home/laurence/Documents/CCPNMR/ccpnmr/ccpnmr1.0/python/ccpnmr/analysis/Analysis.py", line 83, in <module>
    from memops.c.MemCache import MemCache
ImportError: No module named MemCache
>>>                               


Iv come to the end of my knowledge here, is it because i have not installed the files correctly?

Anyhelp would be most appreciated.

Laurence

---

