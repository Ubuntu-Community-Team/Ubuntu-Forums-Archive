---
title: "Cant expand XP partition"
date: 2008-07-11
forum: General Help
---

### Post by JaggedOne on 2008-07-11
Whenever I try I get this error. Any idea how to get around it?


```

GParted 0.3.3

Libparted 1.7.1

Check and repair filesystem (ntfs) on /dev/sda2  00:05    ( ERROR )
     	
calibrate /dev/sda2  00:00    ( SUCCES )
     	
path: /dev/sda2
start: 272108970
end: 374796449
size: 102687480 (48.97 GiB)
check filesystem on /dev/sda2 for errors and (if possible) fix them  00:05    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 52575986176 bytes (52576 MB)
Current device size: 52575989760 bytes (52576 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 6035953 (0x5c19f1): extra cluster in $Bitmap
Cluster accounting failed at 6035954 (0x5c19f2): extra cluster in $Bitmap
Cluster accounting failed at 6035955 (0x5c19f3): extra cluster in $Bitmap
Cluster accounting failed at 6035956 (0x5c19f4): extra cluster in $Bitmap
Cluster accounting failed at 6035957 (0x5c19f5): extra cluster in $Bitmap
Cluster accounting failed at 6035958 (0x5c19f6): extra cluster in $Bitmap
Cluster accounting failed at 6035959 (0x5c19f7): extra cluster in $Bitmap
Cluster accounting failed at 6035960 (0x5c19f8): extra cluster in $Bitmap
Cluster accounting failed at 6035961 (0x5c19f9): extra cluster in $Bitmap
Cluster accounting failed at 6035962 (0x5c19fa): extra cluster in $Bitmap
Cluster accounting failed at 6035963 (0x5c19fb): extra cluster in $Bitmap
Cluster accounting failed at 6035964 (0x5c19fc): extra cluster in $Bitmap
Cluster accounting failed at 6035965 (0x5c19fd): extra cluster in $Bitmap
Cluster accounting failed at 6035966 (0x5c19fe): extra cluster in $Bitmap
Cluster accounting failed at 6035967 (0x5c19ff): extra cluster in $Bitmap
Cluster accounting failed at 6035968 (0x5c1a00): extra cluster in $Bitmap
Cluster accounting failed at 6035969 (0x5c1a01): extra cluster in $Bitmap
Cluster accounting failed at 6035970 (0x5c1a02): extra cluster in $Bitmap
Cluster accounting failed at 6035971 (0x5c1a03): extra cluster in $Bitmap
Cluster accounting failed at 6035972 (0x5c1a04): extra cluster in $Bitmap
Cluster accounting failed at 6035973 (0x5c1a05): extra cluster in $Bitmap
Cluster accounting failed at 6035974 (0x5c1a06): extra cluster in $Bitmap
Cluster accounting failed at 6035975 (0x5c1a07): extra cluster in $Bitmap
Cluster accounting failed at 6035976 (0x5c1a08): extra cluster in $Bitmap
Cluster accounting failed at 6035977 (0x5c1a09): extra cluster in $Bitmap
Cluster accounting failed at 6035978 (0x5c1a0a): extra cluster in $Bitmap
Cluster accounting failed at 6035979 (0x5c1a0b): extra cluster in $Bitmap
Cluster accounting failed at 6035980 (0x5c1a0c): extra cluster in $Bitmap
Cluster accounting failed at 6035981 (0x5c1a0d): extra cluster in $Bitmap
Cluster accounting failed at 6035982 (0x5c1a0e): extra cluster in $Bitmap
Cluster accounting failed at 6035983 (0x5c1a0f): extra cluster in $Bitmap
Cluster accounting failed at 6035984 (0x5c1a10): extra cluster in $Bitmap
Cluster accounting failed at 6035985 (0x5c1a11): extra cluster in $Bitmap
Cluster accounting failed at 6035986 (0x5c1a12): extra cluster in $Bitmap
Cluster accounting failed at 6035987 (0x5c1a13): extra cluster in $Bitmap
Cluster accounting failed at 6035988 (0x5c1a14): extra cluster in $Bitmap
Cluster accounting failed at 6035989 (0x5c1a15): extra cluster in $Bitmap
Cluster accounting failed at 6035990 (0x5c1a16): extra cluster in $Bitmap
Cluster accounting failed at 6035991 (0x5c1a17): extra cluster in $Bitmap
Cluster accounting failed at 6035992 (0x5c1a18): extra cluster in $Bitmap
Cluster accounting failed at 6035993 (0x5c1a19): extra cluster in $Bitmap
Cluster accounting failed at 6035994 (0x5c1a1a): extra cluster in $Bitmap
Cluster accounting failed at 6035995 (0x5c1a1b): extra cluster in $Bitmap
Cluster accounting failed at 6035996 (0x5c1a1c): extra cluster in $Bitmap
Cluster accounting failed at 6035997 (0x5c1a1d): extra cluster in $Bitmap
Cluster accounting failed at 6035998 (0x5c1a1e): extra cluster in $Bitmap
Cluster accounting failed at 6035999 (0x5c1a1f): extra cluster in $Bitmap
Cluster accounting failed at 6036000 (0x5c1a20): extra cluster in $Bitmap
Cluster accounting failed at 6036001 (0x5c1a21): extra cluster in $Bitmap
Cluster accounting failed at 6036002 (0x5c1a22): extra cluster in $Bitmap
Cluster accounting failed at 6036003 (0x5c1a23): extra cluster in $Bitmap
Cluster accounting failed at 6036004 (0x5c1a24): extra cluster in $Bitmap
Cluster accounting failed at 6036005 (0x5c1a25): extra cluster in $Bitmap
Cluster accounting failed at 6036006 (0x5c1a26): extra cluster in $Bitmap
Cluster accounting failed at 6036007 (0x5c1a27): extra cluster in $Bitmap
Cluster accounting failed at 6036008 (0x5c1a28): extra cluster in $Bitmap
Cluster accounting failed at 6036009 (0x5c1a29): extra cluster in $Bitmap
Cluster accounting failed at 6036010 (0x5c1a2a): extra cluster in $Bitmap
Cluster accounting failed at 6036011 (0x5c1a2b): extra cluster in $Bitmap
Cluster accounting failed at 6036012 (0x5c1a2c): extra cluster in $Bitmap
Cluster accounting failed at 6036013 (0x5c1a2d): extra cluster in $Bitmap
Cluster accounting failed at 6036014 (0x5c1a2e): extra cluster in $Bitmap
Cluster accounting failed at 6036015 (0x5c1a2f): extra cluster in $Bitmap
Cluster accounting failed at 6036016 (0x5c1a30): extra cluster in $Bitmap
Cluster accounting failed at 6036017 (0x5c1a31): extra cluster in $Bitmap
Cluster accounting failed at 6036018 (0x5c1a32): extra cluster in $Bitmap
Cluster accounting failed at 6036019 (0x5c1a33): extra cluster in $Bitmap
Cluster accounting failed at 6036020 (0x5c1a34): extra cluster in $Bitmap
Cluster accounting failed at 6036021 (0x5c1a35): extra cluster in $Bitmap
Cluster accounting failed at 6036022 (0x5c1a36): extra cluster in $Bitmap
Cluster accounting failed at 6036023 (0x5c1a37): extra cluster in $Bitmap
Cluster accounting failed at 6036024 (0x5c1a38): extra cluster in $Bitmap
Cluster accounting failed at 6036025 (0x5c1a39): extra cluster in $Bitmap
Cluster accounting failed at 6036026 (0x5c1a3a): extra cluster in $Bitmap
Cluster accounting failed at 6036027 (0x5c1a3b): extra cluster in $Bitmap
Cluster accounting failed at 6036028 (0x5c1a3c): extra cluster in $Bitmap
Cluster accounting failed at 6036029 (0x5c1a3d): extra cluster in $Bitmap
Cluster accounting failed at 6036030 (0x5c1a3e): extra cluster in $Bitmap
Cluster accounting failed at 6036031 (0x5c1a3f): extra cluster in $Bitmap
Cluster accounting failed at 6036032 (0x5c1a40): extra cluster in $Bitmap
Cluster accounting failed at 6036033 (0x5c1a41): extra cluster in $Bitmap
Cluster accounting failed at 6036034 (0x5c1a42): extra cluster in $Bitmap
Cluster accounting failed at 6036035 (0x5c1a43): extra cluster in $Bitmap
Cluster accounting failed at 6036036 (0x5c1a44): extra cluster in $Bitmap
Cluster accounting failed at 6036037 (0x5c1a45): extra cluster in $Bitmap
Cluster accounting failed at 6036038 (0x5c1a46): extra cluster in $Bitmap
Cluster accounting failed at 6036039 (0x5c1a47): extra cluster in $Bitmap
Cluster accounting failed at 6036040 (0x5c1a48): extra cluster in $Bitmap
Cluster accounting failed at 6036041 (0x5c1a49): extra cluster in $Bitmap
Cluster accounting failed at 6036042 (0x5c1a4a): extra cluster in $Bitmap
Cluster accounting failed at 6036043 (0x5c1a4b): extra cluster in $Bitmap
Cluster accounting failed at 6036044 (0x5c1a4c): extra cluster in $Bitmap
Cluster accounting failed at 6036045 (0x5c1a4d): extra cluster in $Bitmap
Cluster accounting failed at 6036046 (0x5c1a4e): extra cluster in $Bitmap
Cluster accounting failed at 6036047 (0x5c1a4f): extra cluster in $Bitmap
Cluster accounting failed at 6036048 (0x5c1a50): extra cluster in $Bitmap
Cluster accounting failed at 6036049 (0x5c1a51): extra cluster in $Bitmap
Cluster accounting failed at 6036050 (0x5c1a52): extra cluster in $Bitmap
Cluster accounting failed at 6036051 (0x5c1a53): extra cluster in $Bitmap
Cluster accounting failed at 6036052 (0x5c1a54): extra cluster in $Bitmap
Cluster accounting failed at 6036053 (0x5c1a55): extra cluster in $Bitmap
Cluster accounting failed at 6036054 (0x5c1a56): extra cluster in $Bitmap
Cluster accounting failed at 6036055 (0x5c1a57): extra cluster in $Bitmap
Cluster accounting failed at 6036056 (0x5c1a58): extra cluster in $Bitmap
Cluster accounting failed at 6036057 (0x5c1a59): extra cluster in $Bitmap
Cluster accounting failed at 6036058 (0x5c1a5a): extra cluster in $Bitmap
Cluster accounting failed at 6036059 (0x5c1a5b): extra cluster in $Bitmap
Cluster accounting failed at 6036060 (0x5c1a5c): extra cluster in $Bitmap
Cluster accounting failed at 6036061 (0x5c1a5d): extra cluster in $Bitmap
Cluster accounting failed at 6036062 (0x5c1a5e): extra cluster in $Bitmap
Cluster accounting failed at 6036063 (0x5c1a5f): extra cluster in $Bitmap
Cluster accounting failed at 6036064 (0x5c1a60): extra cluster in $Bitmap
Cluster accounting failed at 6036065 (0x5c1a61): extra cluster in $Bitmap
Cluster accounting failed at 6036066 (0x5c1a62): extra cluster in $Bitmap
Cluster accounting failed at 6036067 (0x5c1a63): extra cluster in $Bitmap
Cluster accounting failed at 6036068 (0x5c1a64): extra cluster in $Bitmap
Cluster accounting failed at 6036069 (0x5c1a65): extra cluster in $Bitmap
Cluster accounting failed at 6036070 (0x5c1a66): extra cluster in $Bitmap
Cluster accounting failed at 6036071 (0x5c1a67): extra cluster in $Bitmap
Cluster accounting failed at 6036072 (0x5c1a68): extra cluster in $Bitmap
Cluster accounting failed at 6036073 (0x5c1a69): extra cluster in $Bitmap
Cluster accounting failed at 6036074 (0x5c1a6a): extra cluster in $Bitmap
Cluster accounting failed at 6036075 (0x5c1a6b): extra cluster in $Bitmap
Cluster accounting failed at 6036076 (0x5c1a6c): extra cluster in $Bitmap
Cluster accounting failed at 6036077 (0x5c1a6d): extra cluster in $Bitmap
Cluster accounting failed at 6036078 (0x5c1a6e): extra cluster in $Bitmap
Cluster accounting failed at 6036079 (0x5c1a6f): extra cluster in $Bitmap
Cluster accounting failed at 6036080 (0x5c1a70): extra cluster in $Bitmap
Cluster accounting failed at 6036081 (0x5c1a71): extra cluster in $Bitmap
Cluster accounting failed at 6036082 (0x5c1a72): extra cluster in $Bitmap
Cluster accounting failed at 6036083 (0x5c1a73): extra cluster in $Bitmap
Cluster accounting failed at 6036084 (0x5c1a74): extra cluster in $Bitmap
Cluster accounting failed at 6036085 (0x5c1a75): extra cluster in $Bitmap
Cluster accounting failed at 6036086 (0x5c1a76): extra cluster in $Bitmap
Cluster accounting failed at 6036087 (0x5c1a77): extra cluster in $Bitmap
Cluster accounting failed at 6036088 (0x5c1a78): extra cluster in $Bitmap
Cluster accounting failed at 6036089 (0x5c1a79): extra cluster in $Bitmap
Cluster accounting failed at 6036090 (0x5c1a7a): extra cluster in $Bitmap
Cluster accounting failed at 6036091 (0x5c1a7b): extra cluster in $Bitmap
Cluster accounting failed at 6036092 (0x5c1a7c): extra cluster in $Bitmap
Cluster accounting failed at 6036093 (0x5c1a7d): extra cluster in $Bitmap
Cluster accounting failed at 6036094 (0x5c1a7e): extra cluster in $Bitmap
Cluster accounting failed at 6036095 (0x5c1a7f): extra cluster in $Bitmap
Cluster accounting failed at 6036096 (0x5c1a80): extra cluster in $Bitmap
Cluster accounting failed at 6036097 (0x5c1a81): extra cluster in $Bitmap
Cluster accounting failed at 6036098 (0x5c1a82): extra cluster in $Bitmap
Cluster accounting failed at 6036099 (0x5c1a83): extra cluster in $Bitmap
Cluster accounting failed at 6036100 (0x5c1a84): extra cluster in $Bitmap
Cluster accounting failed at 6036101 (0x5c1a85): extra cluster in $Bitmap
Cluster accounting failed at 6036102 (0x5c1a86): extra cluster in $Bitmap
Cluster accounting failed at 6036103 (0x5c1a87): extra cluster in $Bitmap
Cluster accounting failed at 6036104 (0x5c1a88): extra cluster in $Bitmap
Cluster accounting failed at 6036105 (0x5c1a89): extra cluster in $Bitmap
Cluster accounting failed at 6036106 (0x5c1a8a): extra cluster in $Bitmap
Cluster accounting failed at 6036107 (0x5c1a8b): extra cluster in $Bitmap
Cluster accounting failed at 6036108 (0x5c1a8c): extra cluster in $Bitmap
Cluster accounting failed at 6036109 (0x5c1a8d): extra cluster in $Bitmap
Cluster accounting failed at 6036110 (0x5c1a8e): extra cluster in $Bitmap
Cluster accounting failed at 6036111 (0x5c1a8f): extra cluster in $Bitmap
Cluster accounting failed at 6036112 (0x5c1a90): extra cluster in $Bitmap
Cluster accounting failed at 6036209 (0x5c1af1): extra cluster in $Bitmap
Cluster accounting failed at 6036210 (0x5c1af2): extra cluster in $Bitmap
Cluster accounting failed at 6036211 (0x5c1af3): extra cluster in $Bitmap
Cluster accounting failed at 6036212 (0x5c1af4): extra cluster in $Bitmap
Cluster accounting failed at 6036213 (0x5c1af5): extra cluster in $Bitmap
Cluster accounting failed at 6036214 (0x5c1af6): extra cluster in $Bitmap
Cluster accounting failed at 6036215 (0x5c1af7): extra cluster in $Bitmap
Cluster accounting failed at 6036216 (0x5c1af8): extra cluster in $Bitmap
Cluster accounting failed at 6036217 (0x5c1af9): extra cluster in $Bitmap
Cluster accounting failed at 6036218 (0x5c1afa): extra cluster in $Bitmap
Cluster accounting failed at 6036219 (0x5c1afb): extra cluster in $Bitmap
Cluster accounting failed at 6036220 (0x5c1afc): extra cluster in $Bitmap
Cluster accounting failed at 6036221 (0x5c1afd): extra cluster in $Bitmap
Cluster accounting failed at 6036222 (0x5c1afe): extra cluster in $Bitmap
Cluster accounting failed at 6036223 (0x5c1aff): extra cluster in $Bitmap
Cluster accounting failed at 6036224 (0x5c1b00): extra cluster in $Bitmap
Cluster accounting failed at 6036225 (0x5c1b01): extra cluster in $Bitmap
Cluster accounting failed at 6036226 (0x5c1b02): extra cluster in $Bitmap
Cluster accounting failed at 6036227 (0x5c1b03): extra cluster in $Bitmap
Cluster accounting failed at 6036228 (0x5c1b04): extra cluster in $Bitmap
Cluster accounting failed at 6036229 (0x5c1b05): extra cluster in $Bitmap
Cluster accounting failed at 6036230 (0x5c1b06): extra cluster in $Bitmap
Cluster accounting failed at 6036231 (0x5c1b07): extra cluster in $Bitmap
Cluster accounting failed at 6036232 (0x5c1b08): extra cluster in $Bitmap
Cluster accounting failed at 6036233 (0x5c1b09): extra cluster in $Bitmap
Cluster accounting failed at 6036234 (0x5c1b0a): extra cluster in $Bitmap
Cluster accounting failed at 6036235 (0x5c1b0b): extra cluster in $Bitmap
Cluster accounting failed at 6036236 (0x5c1b0c): extra cluster in $Bitmap
Cluster accounting failed at 6036237 (0x5c1b0d): extra cluster in $Bitmap
Cluster accounting failed at 6036238 (0x5c1b0e): extra cluster in $Bitmap
Cluster accounting failed at 6036239 (0x5c1b0f): extra cluster in $Bitmap
Cluster accounting failed at 6036240 (0x5c1b10): extra cluster in $Bitmap
Cluster accounting failed at 6036241 (0x5c1b11): extra cluster in $Bitmap
Cluster accounting failed at 6036242 (0x5c1b12): extra cluster in $Bitmap
Cluster accounting failed at 6036243 (0x5c1b13): extra cluster in $Bitmap
Cluster accounting failed at 6036244 (0x5c1b14): extra cluster in $Bitmap
Cluster accounting failed at 6036245 (0x5c1b15): extra cluster in $Bitmap
Cluster accounting failed at 6036246 (0x5c1b16): extra cluster in $Bitmap
Cluster accounting failed at 6036247 (0x5c1b17): extra cluster in $Bitmap
Cluster accounting failed at 6036248 (0x5c1b18): extra cluster in $Bitmap
Cluster accounting failed at 6036249 (0x5c1b19): extra cluster in $Bitmap
Cluster accounting failed at 6036250 (0x5c1b1a): extra cluster in $Bitmap
Cluster accounting failed at 6036251 (0x5c1b1b): extra cluster in $Bitmap
Cluster accounting failed at 6036252 (0x5c1b1c): extra cluster in $Bitmap
Cluster accounting failed at 6036253 (0x5c1b1d): extra cluster in $Bitmap
Cluster accounting failed at 6036254 (0x5c1b1e): extra cluster in $Bitmap
Cluster accounting failed at 6036255 (0x5c1b1f): extra cluster in $Bitmap
Cluster accounting failed at 6036256 (0x5c1b20): extra cluster in $Bitmap
Cluster accounting failed at 6036257 (0x5c1b21): extra cluster in $Bitmap
Cluster accounting failed at 6036258 (0x5c1b22): extra cluster in $Bitmap
Cluster accounting failed at 6036259 (0x5c1b23): extra cluster in $Bitmap
Cluster accounting failed at 6036260 (0x5c1b24): extra cluster in $Bitmap
Cluster accounting failed at 6036261 (0x5c1b25): extra cluster in $Bitmap
Cluster accounting failed at 6036262 (0x5c1b26): extra cluster in $Bitmap
Cluster accounting failed at 6036263 (0x5c1b27): extra cluster in $Bitmap
Cluster accounting failed at 6036264 (0x5c1b28): extra cluster in $Bitmap
Cluster accounting failed at 6036265 (0x5c1b29): extra cluster in $Bitmap
Cluster accounting failed at 6036266 (0x5c1b2a): extra cluster in $Bitmap
Cluster accounting failed at 6036267 (0x5c1b2b): extra cluster in $Bitmap
Cluster accounting failed at 6036268 (0x5c1b2c): extra cluster in $Bitmap
Cluster accounting failed at 6036269 (0x5c1b2d): extra cluster in $Bitmap
Cluster accounting failed at 6036270 (0x5c1b2e): extra cluster in $Bitmap
Cluster accounting failed at 6036271 (0x5c1b2f): extra cluster in $Bitmap
Cluster accounting failed at 6036272 (0x5c1b30): extra cluster in $Bitmap
Cluster accounting failed at 6036273 (0x5c1b31): extra cluster in $Bitmap
Cluster accounting failed at 6036274 (0x5c1b32): extra cluster in $Bitmap
Cluster accounting failed at 6036275 (0x5c1b33): extra cluster in $Bitmap
Cluster accounting failed at 6036276 (0x5c1b34): extra cluster in $Bitmap
Cluster accounting failed at 6036277 (0x5c1b35): extra cluster in $Bitmap
Cluster accounting failed at 6036278 (0x5c1b36): extra cluster in $Bitmap
Cluster accounting failed at 6036279 (0x5c1b37): extra cluster in $Bitmap
Cluster accounting failed at 6036280 (0x5c1b38): extra cluster in $Bitmap
Cluster accounting failed at 6036281 (0x5c1b39): extra cluster in $Bitmap
Cluster accounting failed at 6036282 (0x5c1b3a): extra cluster in $Bitmap
Cluster accounting failed at 6036283 (0x5c1b3b): extra cluster in $Bitmap
Cluster accounting failed at 6036284 (0x5c1b3c): extra cluster in $Bitmap
Cluster accounting failed at 6036285 (0x5c1b3d): extra cluster in $Bitmap
Cluster accounting failed at 6036286 (0x5c1b3e): extra cluster in $Bitmap
Cluster accounting failed at 6036287 (0x5c1b3f): extra cluster in $Bitmap
Cluster accounting failed at 6036288 (0x5c1b40): extra cluster in $Bitmap
Cluster accounting failed at 6036289 (0x5c1b41): extra cluster in $Bitmap
Cluster accounting failed at 6036290 (0x5c1b42): extra cluster in $Bitmap
Cluster accounting failed at 6036291 (0x5c1b43): extra cluster in $Bitmap
Cluster accounting failed at 6036292 (0x5c1b44): extra cluster in $Bitmap
Cluster accounting failed at 6036293 (0x5c1b45): extra cluster in $Bitmap
Cluster accounting failed at 6036294 (0x5c1b46): extra cluster in $Bitmap
Cluster accounting failed at 6036295 (0x5c1b47): extra cluster in $Bitmap
Cluster accounting failed at 6036296 (0x5c1b48): extra cluster in $Bitmap
Cluster accounting failed at 6036297 (0x5c1b49): extra cluster in $Bitmap
Cluster accounting failed at 6036298 (0x5c1b4a): extra cluster in $Bitmap
Cluster accounting failed at 6036299 (0x5c1b4b): extra cluster in $Bitmap
Cluster accounting failed at 6036300 (0x5c1b4c): extra cluster in $Bitmap
Cluster accounting failed at 6036301 (0x5c1b4d): extra cluster in $Bitmap
Cluster accounting failed at 6036302 (0x5c1b4e): extra cluster in $Bitmap
Cluster accounting failed at 6036303 (0x5c1b4f): extra cluster in $Bitmap
Cluster accounting failed at 6036304 (0x5c1b50): extra cluster in $Bitmap
Cluster accounting failed at 6036305 (0x5c1b51): extra cluster in $Bitmap
Cluster accounting failed at 6036306 (0x5c1b52): extra cluster in $Bitmap
Cluster accounting failed at 6036307 (0x5c1b53): extra cluster in $Bitmap
Cluster accounting failed at 6036308 (0x5c1b54): extra cluster in $Bitmap
Cluster accounting failed at 6036309 (0x5c1b55): extra cluster in $Bitmap
Cluster accounting failed at 6036310 (0x5c1b56): extra cluster in $Bitmap
Cluster accounting failed at 6036311 (0x5c1b57): extra cluster in $Bitmap
Cluster accounting failed at 6036312 (0x5c1b58): extra cluster in $Bitmap
Cluster accounting failed at 6036313 (0x5c1b59): extra cluster in $Bitmap
Cluster accounting failed at 6036314 (0x5c1b5a): extra cluster in $Bitmap
Cluster accounting failed at 6036315 (0x5c1b5b): extra cluster in $Bitmap
Cluster accounting failed at 6036316 (0x5c1b5c): extra cluster in $Bitmap
Cluster accounting failed at 6036317 (0x5c1b5d): extra cluster in $Bitmap
Cluster accounting failed at 6036318 (0x5c1b5e): extra cluster in $Bitmap
Cluster accounting failed at 6036319 (0x5c1b5f): extra cluster in $Bitmap
Cluster accounting failed at 6036320 (0x5c1b60): extra cluster in $Bitmap
Cluster accounting failed at 6036321 (0x5c1b61): extra cluster in $Bitmap
Cluster accounting failed at 6036322 (0x5c1b62): extra cluster in $Bitmap
Cluster accounting failed at 6036323 (0x5c1b63): extra cluster in $Bitmap
Cluster accounting failed at 6036324 (0x5c1b64): extra cluster in $Bitmap
Cluster accounting failed at 6036325 (0x5c1b65): extra cluster in $Bitmap
Cluster accounting failed at 6036326 (0x5c1b66): extra cluster in $Bitmap
Cluster accounting failed at 6036327 (0x5c1b67): extra cluster in $Bitmap
Cluster accounting failed at 6036328 (0x5c1b68): extra cluster in $Bitmap
Cluster accounting failed at 6036329 (0x5c1b69): extra cluster in $Bitmap
Cluster accounting failed at 6036330 (0x5c1b6a): extra cluster in $Bitmap
Cluster accounting failed at 6036331 (0x5c1b6b): extra cluster in $Bitmap
Cluster accounting failed at 6036332 (0x5c1b6c): extra cluster in $Bitmap
Cluster accounting failed at 6036333 (0x5c1b6d): extra cluster in $Bitmap
Cluster accounting failed at 6036334 (0x5c1b6e): extra cluster in $Bitmap
Cluster accounting failed at 6036335 (0x5c1b6f): extra cluster in $Bitmap
Cluster accounting failed at 6036336 (0x5c1b70): extra cluster in $Bitmap
Cluster accounting failed at 6036337 (0x5c1b71): extra cluster in $Bitmap
Cluster accounting failed at 6036338 (0x5c1b72): extra cluster in $Bitmap
Cluster accounting failed at 6036339 (0x5c1b73): extra cluster in $Bitmap
Cluster accounting failed at 6036340 (0x5c1b74): extra cluster in $Bitmap
Cluster accounting failed at 6036341 (0x5c1b75): extra cluster in $Bitmap
Cluster accounting failed at 6036342 (0x5c1b76): extra cluster in $Bitmap
Cluster accounting failed at 6036343 (0x5c1b77): extra cluster in $Bitmap
Cluster accounting failed at 6036344 (0x5c1b78): extra cluster in $Bitmap
Cluster accounting failed at 6036345 (0x5c1b79): extra cluster in $Bitmap
Cluster accounting failed at 6036346 (0x5c1b7a): extra cluster in $Bitmap
Cluster accounting failed at 6036347 (0x5c1b7b): extra cluster in $Bitmap
Cluster accounting failed at 6036348 (0x5c1b7c): extra cluster in $Bitmap
Cluster accounting failed at 6036349 (0x5c1b7d): extra cluster in $Bitmap
Cluster accounting failed at 6036350 (0x5c1b7e): extra cluster in $Bitmap
Cluster accounting failed at 6036351 (0x5c1b7f): extra cluster in $Bitmap
Cluster accounting failed at 6036352 (0x5c1b80): extra cluster in $Bitmap
Cluster accounting failed at 6036353 (0x5c1b81): extra cluster in $Bitmap
Cluster accounting failed at 6036354 (0x5c1b82): extra cluster in $Bitmap
Cluster accounting failed at 6036355 (0x5c1b83): extra cluster in $Bitmap
Cluster accounting failed at 6036356 (0x5c1b84): extra cluster in $Bitmap
Cluster accounting failed at 6036357 (0x5c1b85): extra cluster in $Bitmap
Cluster accounting failed at 6036358 (0x5c1b86): extra cluster in $Bitmap
Cluster accounting failed at 6036359 (0x5c1b87): extra cluster in $Bitmap
Cluster accounting failed at 6036360 (0x5c1b88): extra cluster in $Bitmap
Cluster accounting failed at 6036361 (0x5c1b89): extra cluster in $Bitmap
Cluster accounting failed at 6036362 (0x5c1b8a): extra cluster in $Bitmap
Cluster accounting failed at 6036363 (0x5c1b8b): extra cluster in $Bitmap
Cluster accounting failed at 6036364 (0x5c1b8c): extra cluster in $Bitmap
Cluster accounting failed at 6036365 (0x5c1b8d): extra cluster in $Bitmap
Cluster accounting failed at 6036366 (0x5c1b8e): extra cluster in $Bitmap
Cluster accounting failed at 6036367 (0x5c1b8f): extra cluster in $Bitmap
Cluster accounting failed at 6036368 (0x5c1b90): extra cluster in $Bitmap
Filesystem check failed! Totally 320 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

========================================

```

Edit: I just saw the note about running chkdsk /f on windows and rebooting twice. I will give that a shot. If it doesnt work Ill post back here.

---

### Post by Bachstelze on 2008-07-11
There seems to be an error in your filesystem, you'lll have to fix it first. Boot windows, open a terminal and do

```
chkdsk c:
```

---

### Post by JaggedOne on 2008-07-11
When I run chkdsk /c it finds the same errors that Gparted finds. (C and F parameters not being specified.) 

Chkdsk made no apparent attempts to fix the errors and ran in read only mode. 

Now what?

---

### Post by cariboo on 2008-07-11
If you are in xp, Start-->Run, type chkdisk /f and hit enter it will ask you if you want to run chkdsk at next boot, choose y, and then reboot. That should repair the problems with your disk.

Jim

---

