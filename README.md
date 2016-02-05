parsecdat
=========

pack, unpack, list and mount parsec .dat archives

File Format
-----------

	┌────────────────────────────────┐
	│                                │
	│ Header                         │
	│                                │
	│    "msh DataPackage\0"         │
	│    number of entries           │
	│    size of index section       │
	│    size of data section        │
	│    end offest/size of archive  │
	│                                │
	├────────────────────────────────┤
	│                                │
	│ Index                          │
	│                                │
	│ ┌────────────────────────────┐ │
	│ │                            │ │
	│ │ Entry                      │ │
	│ │                            │ │
	│ │   name                     │ │
	│ │   offset                   │ │
	│ │   size                     │ │
	│ │                            │ │
	│ └────────────────────────────┘ │
	│ ...                            │
	│                                │
	├────────────────────────────────┤
	│                                │
	│ Data                           │
	│ ...                            │
	│                                │
	└────────────────────────────────┘

### Archive Header

	Offset  Size  Type        Description
	     0    16  char[16]    "msh DataPackage\0"
	    16     4  uint32_t    number of entries
	    20     4  uint32_t    size of index section
	    24     4  uint32_t    size of data section
	    28     4  uint32_t    end offest/size of archive
	    
### Index Entry

	Offset  Size  Type        Description
	     0    16  char[16]    zero padded file name
	    16     4  uint32_t    absolute offset
	    20     4  uint32_t    size
	    24     4  uint32_t    unused (always 0)
	    28     4  uint32_t    unused (always 0)
