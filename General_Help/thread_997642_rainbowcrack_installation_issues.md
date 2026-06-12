---
title: "rainbowcrack installation issues"
date: 2008-11-30
forum: General Help
---

### Post by slipdipper on 2008-11-30
when i try to install rainbowcrack from source i get the following issues. My installation procedures were the same as defined in [http://ubuntuforums.org/showthread.php?t=909946](http://ubuntuforums.org/showthread.php?t=909946) .

Any ideas?
```

$ make -f makefile.linux
g++ Public.cpp ChainWalkContext.cpp HashAlgorithm.cpp HashRoutine.cpp RainbowTableGenerate.cpp -lssl -O3 -o rtgen
In file included from Public.cpp:11:
Public.h:25: error: âuint64â does not name a type
Public.h:26: error: âuint64â does not name a type
Public.h:37: error: âuint64â was not declared in this scope
Public.h:38: error: âuint64â was not declared in this scope
Public.cpp: In function âbool ReadLinesFromFile(std::string, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)â:
Public.cpp:61: warning: ignoring return value of âsize_t fread(void*, size_t, size_t, FILE*)â, declared with attribute warn_unused_result
Public.cpp: At global scope:
Public.cpp:113: error: redefinition of âstd::string uint64tostrâ
Public.h:37: error: âstd::string uint64tostrâ previously declared here
Public.cpp:113: error: âuint64â was not declared in this scope
Public.cpp:126: error: redefinition of âstd::string uint64tohexstrâ
Public.h:38: error: âstd::string uint64tohexstrâ previously declared here
Public.cpp:126: error: âuint64â was not declared in this scope
In file included from ChainWalkContext.h:11,
                 from ChainWalkContext.cpp:11:
Public.h:25: error: âuint64â does not name a type
Public.h:26: error: âuint64â does not name a type
Public.h:37: error: âuint64â was not declared in this scope
Public.h:38: error: âuint64â was not declared in this scope
In file included from ChainWalkContext.cpp:11:
ChainWalkContext.h:30: error: âuint64â does not name a type
ChainWalkContext.h:31: error: âuint64â does not name a type
ChainWalkContext.h:34: error: âuint64â does not name a type
ChainWalkContext.h:37: error: âuint64â does not name a type
ChainWalkContext.h:56: error: âuint64â does not name a type
ChainWalkContext.h:61: error: âuint64â has not been declared
ChainWalkContext.h:68: error: âuint64â does not name a type
ChainWalkContext.cpp:31: error: âuint64â does not name a type
ChainWalkContext.cpp:32: error: âuint64â does not name a type
ChainWalkContext.cpp:35: error: âuint64â does not name a type
ChainWalkContext.cpp: In static member function âstatic bool CChainWalkContext::LoadCharset(std::string)â:
ChainWalkContext.cpp:119: error: âmemcpyâ was not declared in this scope
ChainWalkContext.cpp: In static member function âstatic bool CChainWalkContext::SetPlainCharset(std::string, int, int)â:
ChainWalkContext.cpp:165: error: âm_nPlainSpaceUpToXâ was not declared in this scope
ChainWalkContext.cpp:166: error: âuint64â was not declared in this scope
ChainWalkContext.cpp:166: error: expected `;' before ânTempâ
ChainWalkContext.cpp:170: error: ânTempâ was not declared in this scope
ChainWalkContext.cpp:178: error: âm_nPlainSpaceTotalâ was not declared in this scope
ChainWalkContext.cpp: In static member function âstatic bool CChainWalkContext::SetRainbowTableIndex(int)â:
ChainWalkContext.cpp:188: error: âm_nReduceOffsetâ was not declared in this scope
ChainWalkContext.cpp: At global scope:
ChainWalkContext.cpp:303: error: âuint64â does not name a type
ChainWalkContext.cpp: In static member function âstatic void CChainWalkContext::Dump()â:
ChainWalkContext.cpp:339: error: âm_nPlainSpaceTotalâ was not declared in this scope
ChainWalkContext.cpp:342: error: âm_nReduceOffsetâ was not declared in this scope
ChainWalkContext.cpp: In member function âvoid CChainWalkContext::GenerateRandomIndex()â:
ChainWalkContext.cpp:348: error: âm_nIndexâ was not declared in this scope
ChainWalkContext.cpp:349: error: âm_nPlainSpaceTotalâ was not declared in this scope
ChainWalkContext.cpp: At global scope:
ChainWalkContext.cpp:352: error: variable or field âSetIndexâ declared void
ChainWalkContext.cpp:352: error: âuint64â was not declared in this scope
ChainWalkContext.cpp: In member function âvoid CChainWalkContext::SetHash(unsigned char*)â:
ChainWalkContext.cpp:359: error: âmemcpyâ was not declared in this scope
ChainWalkContext.cpp: In member function âvoid CChainWalkContext::IndexToPlain()â:
ChainWalkContext.cpp:367: error: âm_nIndexâ was not declared in this scope
ChainWalkContext.cpp:367: error: âm_nPlainSpaceUpToXâ was not declared in this scope
ChainWalkContext.cpp:374: error: âuint64â was not declared in this scope
ChainWalkContext.cpp:374: error: expected `;' before ânIndexOfXâ
ChainWalkContext.cpp:392: error: ânIndexOfXâ was not declared in this scope
ChainWalkContext.cpp:396: error: ânIndexOfXâ was not declared in this scope
ChainWalkContext.cpp:399: error: ânIndexOfXâ was not declared in this scope
ChainWalkContext.cpp: In member function âvoid CChainWalkContext::HashToIndex(int)â:
ChainWalkContext.cpp:438: error: âm_nIndexâ was not declared in this scope
ChainWalkContext.cpp:438: error: âuint64â was not declared in this scope
ChainWalkContext.cpp:438: error: expected primary-expression before â)â token
ChainWalkContext.cpp:438: error: expected `)' before âm_Hashâ
ChainWalkContext.cpp: At global scope:
ChainWalkContext.cpp:441: error: âuint64â does not name a type
ChainWalkContext.cpp: In member function âbool CChainWalkContext::CheckHash(unsigned char*)â:
ChainWalkContext.cpp:491: error: âmemcmpâ was not declared in this scope
In file included from HashAlgorithm.cpp:9:
Public.h:25: error: âuint64â does not name a type
Public.h:26: error: âuint64â does not name a type
Public.h:37: error: âuint64â was not declared in this scope
Public.h:38: error: âuint64â was not declared in this scope
In file included from ChainWalkContext.h:11,
                 from RainbowTableGenerate.cpp:18:
Public.h:25: error: âuint64â does not name a type
Public.h:26: error: âuint64â does not name a type
Public.h:37: error: âuint64â was not declared in this scope
Public.h:38: error: âuint64â was not declared in this scope
In file included from RainbowTableGenerate.cpp:18:
ChainWalkContext.h:30: error: âuint64â does not name a type
ChainWalkContext.h:31: error: âuint64â does not name a type
ChainWalkContext.h:34: error: âuint64â does not name a type
ChainWalkContext.h:37: error: âuint64â does not name a type
ChainWalkContext.h:56: error: âuint64â does not name a type
ChainWalkContext.h:61: error: âuint64â has not been declared
ChainWalkContext.h:68: error: âuint64â does not name a type
RainbowTableGenerate.cpp: In function âint main(int, char**)â:
RainbowTableGenerate.cpp:113: error: âstrcmpâ was not declared in this scope
RainbowTableGenerate.cpp:115: error: âatoiâ was not declared in this scope
RainbowTableGenerate.cpp:128: error: âatoiâ was not declared in this scope
RainbowTableGenerate.cpp:207: error: âuint64â was not declared in this scope
RainbowTableGenerate.cpp:207: error: expected `;' before ânIndexâ
RainbowTableGenerate.cpp:208: error: ânIndexâ was not declared in this scope
RainbowTableGenerate.cpp:222: error: ânIndexâ was not declared in this scope
RainbowTableGenerate.cpp:222: error: âclass CChainWalkContextâ has no member named âGetIndexâ
RainbowTableGenerate.cpp:163: warning: ignoring return value of âint nice(int)â, declared with attribute warn_unused_result
make: *** [rtgen] Error 1
$

```

---

### Post by jmarsden on 2008-11-30
Adding two lines to src/Public.h fixes the compile errors.

After #include <list>  add:

#include <cstring>
#include <stdlib.h>

---

### Post by slipdipper on 2008-11-30
Thanks to jmarsden from #nubuntu for the fix. 

just need to 

modify src/Public.h and add the following lines to the include statements:

```

#include <cstring>
#include <stdlib.h>

```

Full installation instructions are:

Download sources:
```

wget http://www.antsight.com/zsl/rainbowcrack/rainbowcrack-1.2-src.zip
wget http://www.antsight.com/zsl/rainbowcrack/rainbowcrack-1.2-src-algorithmpatch.zip

```

Install Depends:
```

sudo aptitude install build-essential openssl libssl-dev unzip

```

Unzip:
```

unzip rainbowcrack-1.2-src-algorithmpatch.zip
unzip rainbowcrack-1.2-src.zip

```

Copy patches:
```
 
cp rainbowcrack-1.2-src-algorithmpatch/* rainbowcrack-1.2-src/src/

```

Enter directory:
```

cd rainbowcrack-1.2-src/src/

```

(Required) Edit Public.h and add below lines above "using namespace std;"
```

#include <cstring>
#include <stdlib.h>

```

(Optional) Edit Public.h and add lines above "#define uint64 u_int64_t" 
```

#include <sys/types.h>

```

Compile:
```

make -f makefile.linux

```

Install:
```
 
sudo cp rcrack rtdump rtgen rtsort /usr/bin

```

Errors will still happen during compile, what i see is below, doesnt appear to cause issues so far:

```

$ make -f makefile.linux
g++ Public.cpp ChainWalkContext.cpp HashAlgorithm.cpp HashRoutine.cpp RainbowTableGenerate.cpp -lssl -O3 -o rtgen
Public.cpp: In function âbool ReadLinesFromFile(std::string, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)â:
Public.cpp:61: warning: ignoring return value of âsize_t fread(void*, size_t, size_t, FILE*)â, declared with attribute warn_unused_result
Public.cpp: In function âstd::string uint64tostr(u_int64_t)â:
Public.cpp:120: warning: format â%lluâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
Public.cpp: In function âstd::string uint64tohexstr(u_int64_t)â:
Public.cpp:133: warning: format â%016llxâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
RainbowTableGenerate.cpp: In function âint main(int, char**)â:
RainbowTableGenerate.cpp:163: warning: ignoring return value of âint nice(int)â, declared with attribute warn_unused_result
g++ Public.cpp ChainWalkContext.cpp HashAlgorithm.cpp HashRoutine.cpp RainbowTableDump.cpp -lssl -o rtdump
Public.cpp: In function âstd::string uint64tostr(u_int64_t)â:
Public.cpp:120: warning: format â%lluâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
Public.cpp: In function âstd::string uint64tohexstr(u_int64_t)â:
Public.cpp:133: warning: format â%016llxâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
g++ Public.cpp RainbowTableSort.cpp -o rtsort
Public.cpp: In function âstd::string uint64tostr(u_int64_t)â:
Public.cpp:120: warning: format â%lluâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
Public.cpp: In function âstd::string uint64tohexstr(u_int64_t)â:
Public.cpp:133: warning: format â%016llxâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
RainbowTableSort.cpp: In function âint QuickSortPartition(RainbowChain*, int, int)â:
RainbowTableSort.cpp:37: warning: integer overflow in expression
g++ Public.cpp ChainWalkContext.cpp HashAlgorithm.cpp HashRoutine.cpp HashSet.cpp MemoryPool.cpp ChainWalkSet.cpp CrackEngine.cpp RainbowCrack.cpp -lssl -O3 -o rcrack
Public.cpp: In function âbool ReadLinesFromFile(std::string, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)â:
Public.cpp:61: warning: ignoring return value of âsize_t fread(void*, size_t, size_t, FILE*)â, declared with attribute warn_unused_result
Public.cpp: In function âstd::string uint64tostr(u_int64_t)â:
Public.cpp:120: warning: format â%lluâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
Public.cpp: In function âstd::string uint64tohexstr(u_int64_t)â:
Public.cpp:133: warning: format â%016llxâ expects type âlong long unsigned intâ, but argument 3 has type âu_int64_tâ
CrackEngine.cpp: In member function âvoid CCrackEngine::SearchTableChunk(RainbowChain*, int, int, CHashSet&)â:
CrackEngine.cpp:105: warning: format â%dâ expects type âintâ, but argument 2 has type âsize_tâ


```

---

### Post by Hex on 2009-08-23
Fixed my installation problems, thank you!

---

### Post by LexXx on 2010-04-20
Download Link is broken:(((
Help :(

---

