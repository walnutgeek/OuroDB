# OuroDB

Content addressed storgage will be written in GO lang soon. Not much experience with GO but sounds like good lang to invest time.

For now use that readme as scratch paper.

Ideas:

  * Use SHA2 as blob key
  * Split large blobs into chunks. Chunk size is customizible and reffered further as CH_SZ. All chunks will be >= CH_SZ  < 2 * CH_SZ, except if whole blob is smaller that CH_SZ.
  * Boundary of chunk will be choosen based on content with intention that chunck boundaries will end up in same spot and po  reusing chunks. Consider using rolling hash and common pad bytes to deterministically find these chanks in stream.
  * Blobs that fit into one chunk use SHA2 of raw data as key, otherwise SHA2 key of array of SHA2 of chunks.
  * Content of db organized in files. Files are append only. Blobs are splited in chunks and appended to files. Files continuously hashed and referer hashes of previous file creating temper resistant chain (blockchain). File size regulated by MAX_FILE_SZ.
  * Chanks stored in file as blocks. Block contains header followed by raw data. 
  * The block header contains SHA2 of raw data, and chunk size, SHA2 of previous block header or previous file footer.
  * Open file maintain block allocation table in memory, and append it to end of file when file is finshed.
  * Finishing block with reference to begininig of block alloccation table and SHA2 of last block header.
  * Block types: RAW, CATALOG, DELETE,  
  * 

 

