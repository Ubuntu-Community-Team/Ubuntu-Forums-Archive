---
title: "Samsung YP-T10 mp3 player"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by legatek on 2007-12-20
Hello!

I received a brand new Samsung YP-T10 mp3 player and am now trying to read it through Feisty. So far I have been following this thread to get me started:

[http://ubuntuforums.org/showthread.php?t=540577](http://ubuntuforums.org/showthread.php?t=540577)

I downloaded and complied the libmtp source from sourceforge since it supports this model, and running "mtp-detect" in the terminal confirms that it's detected. However, Gnomad2 doesn't recognize it, returning "No jukeboxes found on USB bus". Nor does it mount as an external storage device. What am I doing wrong? The output of mtp-detect is as follows. What concerns me is the large number of read-only fields and the last 5 lines, indicating time outs.

```
libmtp version: 0.2.4

Attempting to connect device(s)
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 508a
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Microsoft device descriptor 0xee:
        0000: 1203 4d00 5300 4600 5400 3100 3000 3000   ..M.S.F.T.1.0.0.
        0010: 0100                                      ..
Device info:
   Manufacturer: SAMSUNG
   Model: T10
   Device version: 1.15
   Serial number: 707091005F125F90907081717222BCD1
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com/WMPPD: 11.0;microsoft.com/WMDRMPD: 10.1;microsoft.com/WMPPD: 10.0;microsoft.com/AAVT: 1.0;microsoft.com/WMDRMND: 1.0;audible.com: 1.0;
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   100b: Delete object
   100c: Send object info
   100d: Send object
   100f: Format storage
   1010: Reset device
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   9810: Get object references
   9811: Set object references
   9802: Get object property description
   9801: Get object properties supported
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   101b: Get partial object
   9201: Report Added/Deleted Items
   9202: Report Acquired Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
   9170: Open Media Session
   9171: Close Media Session
   9172: Get Next Data Block
   9173: Set Current Time Position
   9180: Send Registration Request
   9181: Get Registration Response
   9182: Get Proximity Challenge
   9183: Send Proximity Response
   9184: Send WMDRM-ND License Request
   9185: Get WMDRM-ND License Response
Events supported:
   0x4004
   0x4005
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd103: Revocation Info
Playable File (Object) Types and Object Properties Supported:
   3001: Association/Directory
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc9a: AlbumName STRING data type GET/SET
   3009: MP3
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX 268435456, STEP 1 GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de92: BitRateType UINT16 data type enumeration: 0, 1, 2, 3,  GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
   b901: WMA
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX 268435456, STEP 1 GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de92: BitRateType UINT16 data type enumeration: 0, 1, 2, 3,  GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
   3801: JPEG
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 640, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 640, STEP 1 GET/SET
   b981: WMV
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 320, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 240, STEP 1 GET/SET
      de97: ScanDepth UINT16 data type enumeration: 1,  READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type enumeration: 0, 20000, 25000, 29970, 30000,  GET/SET
      de9b: VideoFourCCCodec UINT32 data type enumeration: 0, 859189832, 958804552, 1195724877, 827739479, 844516695, 861293911,  GET/SET
      de9e: KeyFrameDistance UINT32 data type range: MIN 100, MAX 300, STEP 1 GET/SET
      de9c: VideoBitRate UINT32 data type range: MIN 1, MAX 850000, STEP 1 GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 1, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dea1: EncodingProfile STRING data type GET/SET
   b903: AAC
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX 268435456, STEP 1 GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 1, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de92: BitRateType UINT16 data type enumeration: 0, 1, 2, 3,  GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
   300c: ASF
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 320, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 240, STEP 1 GET/SET
      de97: ScanDepth UINT16 data type enumeration: 1,  READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type enumeration: 0, 20000, 25000, 29970, 30000,  GET/SET
      de9b: VideoFourCCCodec UINT32 data type enumeration: 0, 859189832, 958804552, 1195724877, 827739479, 844516695, 861293911,  GET/SET
      de9e: KeyFrameDistance UINT32 data type range: MIN 100, MAX 300, STEP 1 GET/SET
      de9c: VideoBitRate UINT32 data type range: MIN 1, MAX 850000, STEP 1 GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 1, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dea1: EncodingProfile STRING data type GET/SET
   3001: Association/Directory
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc9a: AlbumName STRING data type GET/SET
   ba05: Abstract Audio Video Playlist
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
   3000: Undefined Type
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
   b802: Firmware
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
   ba03: Abstract Audio Album
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 1000000, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 1000000, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX -1, STEP 1 READ ONLY
      dc9b: AlbumArtist STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 3967680512
      FreeSpaceInBytes: 3872661504
      FreeSpaceInObjects: 11968
      StorageDescription: Internal Storage
      VolumeIdentifier: 707091005F125F90907081717222BCD1
Special directories:
   Default music folder: 0x20000004
   Default playlist folder: 0x20000003
   Default picture folder: 0x20000006
   Default video folder: 0x20000005
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00000000
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: T10
   Synchronization partner: Longhorn Sync Engine
   Battery level 100 of 100 (100%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   JPEG file
   Microsoft Windows Media Video
   Advanced Audio Coding (AAC)/MPEG-2 Part 7/MPEG-4 Part 3
   Microsoft Advanced Systems Format
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20070101 05:37:17Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>AG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">cHCRAF8SX5CQcIFxciK80QAAAAA=</UNIQUEID><PUBLICKEY private="1">Be1R65C/NDvJk7UqHqebhpbT5gDBuSCWzu70CAljEvMkqTTGHX2OIw==</PUBLICKEY><KEYDATA>WpxEav9nvyA8pOwcxHAVvG/EdV4=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>KitqF6P/iPTZrf3rLVrGT6i67k1onoepMRd+NBl9D2xl5ou2eWrjKQ==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>ROnU9zYmZGVUuxYmMjbzZAIi/Aw=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.108.81</SECURITYVERSION><CERTIFICATE private="1">Be1R65C/NDvJk7UqHqebhpbT5gDBuSCWzu70CAljEvMkqTTGHX2OIwIEbFF5xcIpty05H2PU2y6L9YLK9sBkF5JlvwdymZw0IW0B7t7+Pd8v4Xt3</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>YP-T10</NAME><MANUFACTURER>Samsung</MANUFACTURER><MAKE>Samsung</MAKE><DISTRIBUTOR>WorldWideImporters</DISTRIBUTOR><MODEL>YP-T10</MODEL><SECURITYLEVEL>2000</SECURITYLEVEL><HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR><HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR><FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR><FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR><FEATURES><CLOCK>2</CLOCK><SECURECLOCK><URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL><PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY></SECURECLOCK><METERING>1</METERING><LICENSE_ACQ>0</LICENSE_ACQ><LICENSE_SYNC>1</LICENSE_SYNC><ENCRYPTION>0</ENCRYPTION><SYMMETRIC_OPT>1</SYMMETRIC_OPT></FEATURES><LIMITS><MAXCHAINDEPTH>2</MAXCHAINDEPTH><MAXLICENSESIZE>10240</MAXLICENSESIZE><MAXHEADERSIZE>5120</MAXHEADERSIZE></LIMITS><PUBLICKEY>vRW/PPkzAfSzYbHv8LiL7SlduCMIW81dE7wFRuHHwZRIpgo8I6RGWg==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>+leZFfHTUpPiJuxKrZY2NGc/E1NDZTaCFl84wvYcHSHdyMBbTL0AJw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>1973</AUTH_ID><PUBLICKEY>LA99x43GKtSfbrir3YWgsHH/Ih/txGBoe5E8LV4KVNb9uQABohtMDw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>rId2DudMrmY+yzso2pVn0lNzYIHUpiH/CJBb+TvgT7FOGD7omELtGw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>SmPt0XQ5U8r9y+GecoWQ/zMpF2YxJ/6kRzS3tQKbVjUY2kJGVpqoJg==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
WMPInfo.xml Does not exist on this device
PTP: Closing session
inep: usb_get_endpoint_status(): Connection timed out
outep: usb_get_endpoint_status(): Connection timed out
usb_clear_halt() on IN endpoint: Connection timed out
usb_clear_halt() on OUT endpoint: Connection timed out
usb_clear_halt() on INTERRUPT endpoint: Connection timed out
OK.

```

---

### Post by legatek on 2007-12-20
Update:

I followed the tutorial for compiling libmtp and gnomad from source in Edgy in this thread:

[http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)

using the latest versions from sourceforge, and now everything works fine.

---

### Post by chooban on 2007-12-20
I've got the same player but I can't get mine to work with amarok in Gutsy.

I can connect to the device and transfer tracks successfully using mtpfs but I'd rather use amarok as it's a lot simpler and doesn't require changing to root. Unfortunately, amarok just says that it cannot connect to MTP device.

The last line in dmesg says -

**[ 2487.964000] usb 4-1: usbfs: USBDEVFS_CONTROL failed cmd amarokapp rqt 192 rq 1 len 1024 ret -110**

I'm using a self compiled libmtp 0.2.4 and everything else is from the ubuntu repositories. Anyone got any ideas for what to try next? I suspect that it's something to do with permissions but I think having the following in my udev rules file should sort that out -

**SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="508a", GROUP="plugdev", MODE="666"**

**Update** : I can send tracks as my normal login using the mtp-connect command so it's not a permissions issue. :-/

---

### Post by heidfirst on 2007-12-26
Chooban

Thanks for the info here, I can also now transfer files to my T10 using mtp-connect.  I have complied version 0.2.4 of libmtp and amended udev rules and that has at least got the transfer working, hopefully things will work better with 8.04.

Gordon

---

