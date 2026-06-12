---
title: "Creative Zen Micro not detected"
date: 2009-03-27
forum: Hardware
---

### Post by grayamf on 2009-03-27
Hi everyone,

I used to be able to detect my Zen Micro 4GB through Gnomad2, but detection failed after my system upgrade from Heron to Ibex. I've plowed through threads and googled but came up with no viable solution to my problem. Here are some output that might be helpful. Any help or suggestion greatly appreciated.

$ lsusb
Bus 007 Device 017: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 007 Device 016: ID 041e:4157 Creative Technology, Ltd 


$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN (041e:4157) @ bus 0, dev 16
Attempting to connect device(s)
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
usb_claim_interface(): Bad file descriptor
LIBMTP PANIC: Could not open session on device
Unable to open raw device 0
OK.


$sudo mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN (041e:4157) @ bus 0, dev 18
Attempting to connect device(s)
PTP: Opening session
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4157
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 18
      Device entry info:
         Vendor: Creative
         Vendor id: 0x041e
         Product: ZEN
         Vendor id: 0x4157
         Device flags: 0x00000480
Microsoft device descriptor 0xee:
	0000: 1203 4d00 5300 4600 5400 3100 3000 3000	..M.S.F.T.1.0.0.
	0010: fe00                                   	..
Microsoft device response to control message 1, CMD 0xfe:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000                    	........
Microsoft device response to control message 2, CMD 0xfe:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000                    	........
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative ZEN
   Device version: 1.21.01_0.03.01
   Serial number: 4A030000BD4A1B270002D365BE8E5B27
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1012: Set object protection
   1016: Set device property value
   1017: Reset device property value
   1019: Move object
   101b: Get partial object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
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
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b901: WMA
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b904: Audible.com Codec
      da01: unknown(da01) UINT32 data type enumeration: 2, 3, 4,  GET/SET
      da02: unknown(da02) array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: unknown(da03) UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b982: MP4
      de99: AudioWAVECodec UINT32 data type enumeration: 41222,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba03: Abstract Audio Album
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 24576, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba01: Abstract Multimedia Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 3328, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 4992, STEP 1 GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   300a: MS AVI
      de99: AudioWAVECodec UINT32 data type enumeration: 85, 17, 1,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 1536000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 4000000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 844515635, 878070084, 1482049860, 808802372, 1196444237, 1145656920,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 3000000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   300c: ASF
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b981: WMV
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   bb83: vCard3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   be03: vCalendar2
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b802: Firmware
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 3965943808
      FreeSpaceInBytes: 2605088768
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 4A030000BD4A1B270002D365BE8E5B27
Special directories:
   Default music folder: 0x00000057
   Default playlist folder: 0x0000005b
   Default picture folder: 0x00000067
   Default video folder: 0x0000006b
   Default organizer folder: 0x00000063
   Default zencast folder: 0x00000073
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: My Zen
   Synchronization partner: (NULL)
   Battery level 255 of 255 (100%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20080219 03:46:07Z#</VALUE><FLAG>DRM_CLK_NOT_SET</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AAADSicbSr1l0wIAJ1uOvgAAAAA=</UNIQUEID><PUBLICKEY private="1">27xZr9+pinEq3qGMp3Q1CSB2CwYuyAI+TPk5AmhO1gy41XnojDdSFw==</PUBLICKEY><KEYDATA>7w/FDagN12By1fIOMMBR6Dq5+68=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>6YmJiAiD1Jwl4bvHJQjMNCFw1kn8lKWPDP9hg7rb8lW3DCLEAT9aAw==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>hVZI+1OE+56XW/oIZTjROjvl3pA=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.108.193</SECURITYVERSION><CERTIFICATE private="1">27xZr9+pinEq3qGMp3Q1CSB2CwYuyAI+TPk5AmhO1gy41XnojDdSFwIEbMGLeGJiLJ4P/L/oDB5SbI3JgQqOKMI9I/N7EDhIo21b+THe/xKlNule</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative ZEN</NAME>
  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>
  <MODEL>DVP-FL0001</MODEL>
  <SECURITYLEVEL>2000</SECURITYLEVEL>
  <HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR>
  <HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR>
  <FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR>
  <FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR>
  <FEATURES>
    <CLOCK>2</CLOCK>
    <SECURECLOCK>
      <URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL>
      <PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY>
    </SECURECLOCK>
    <METERING>1</METERING>
    <LICENSE_ACQ>0</LICENSE_ACQ>
    <LICENSE_SYNC>1</LICENSE_SYNC>
    <ENCRYPTION>0</ENCRYPTION>
    <SYMMETRIC_OPT>1</SYMMETRIC_OPT>
  </FEATURES>
  <LIMITS>
    <MAXCHAINDEPTH>2</MAXCHAINDEPTH>
    <MAXLICENSESIZE>10240</MAXLICENSESIZE>
    <MAXHEADERSIZE>5120</MAXHEADERSIZE>
  </LIMITS><PUBLICKEY>01jSNo4LLYCkLWpnsvVOxk1wvxbm2krcn20LgpXL9Zf91opCNsMyAQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>DrK/bNN2aO5ImZHdepevdhlT6UePVcdaxTWOMvw/8RYKeQFjSPwWUw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>2085</AUTH_ID><PUBLICKEY>U3xlv/ZHjD1bOwjB+VKpZuAf3UI+x+5XtTYc7TvHKdQeGpyFrOmOEw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>iBzmFZxhy/VC9d2REO5iicO+dguqv8zhB7QPZe0JOj7BNKAwmrQoew==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>Ko25GwcWTT0R8xP4rS9+h4Z/EHX03y7Gb/281mD8U0nQGG3Rk9O+TA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
WMPInfo.xml Does not exist on this device
PTP: Closing session
OK.

---

### Post by bhospadaruk on 2009-04-27
I have tried for weeks to get my Zen Micro to work with Ibex and now Jackalope.  I DID get it to work with Gnomad2 by running under "sudo".

I could never get Rhythmbox or Songbird or anything else to work

Then, just for kicks I loaded the "Play for Sure" firmware from Creative (v2.21.02) and the unit works perfectly now with Rhythmbox.  Also, when I plug it in, you automatically get a nice icon for the Zen on your desktop.

So - the solution was all in the firmware!:guitar:

PS - Gnomad2 now also works without having to use sudo

---

### Post by grayamf on 2009-05-07
I flashed the firmware to 2.21.03. The icon shows up nicely on my desktop whenever the device is plugged. However, Gnomad2 still fails to detect any device on usb. It does not show up on rhythmbox either...*sigh*

---

### Post by evencoil on 2009-05-14
do you know if its possible to flash the firmware from a linux machine? The software on creative's site seems to only work for winxp/vista...?

---

