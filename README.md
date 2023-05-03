Download Link: https://assignmentchef.com/product/solved-cs201-hw1
<br>
This part is a simplified version of the entire system. It stores the artists, titles, and years of musicalbums in a collection without their list of songs. The music albums will be stored in a dynamicallyallocated array of MusicAlbum objects. Thus, you will first implement the MusicAlbum class. Thisclass is rather simple for Part A, but will need to be extended for Part B.1. Below is the required part of the MusicAlbum class. The name of the class should beMusicAlbum; the interface for the class:should be coded in a file called SimpleMusicAlbum.h and its implementation should be codedin a file called SimpleMusicAlbum.cpp.#ifndef __SIMPLE_MUSIC_ALBUM_H#define __SIMPLE_MUSIC_ALBUM_H#include &lt;string&gt;using namespace std;class MusicAlbum {public:MusicAlbum(const string maArtist = “”,const string maTitle = “”,const int maYear = 0);~MusicAlbum();MusicAlbum(const MusicAlbum &amp;maToCopy);void operator=(const MusicAlbum &amp;right);string getMusicAlbumArtist();string getMusicAlbumTitle();int getMusicAlbumYear();private:string artist;string title;int year;};#endif‚Ä¢ The MusicAlbum class should have the data members Artist, Title, and Year. Youshould implement get functions for these data members since they will be used to test yourprogram.‚Ä¢ You should also implement a default constructor that initializes the Artist, Title, and Yeardata members. Additionally, you should implement your own destructor and copy constructor,and overload the assignment operator. Although you may use the default ones for some of thesemember functions, you are advised to implement them (although some may have nostatements) in Part A so that it will be easier for you to extend them in Part B.‚Ä¢ Do not delete or modify any part of the given data members or member functions. However,you may define additional data members and member functions, if necessary.2. Below is the required part of the music album collection (MAC) class that you will code in Part A ofthis assignment. The name of the class should be MAC; the interface for the class:should be coded in a file called SimpleMAC.h and its implementation should be coded in a filecalled SimpleMAC.cpp.‚Ä¢ Implement the default constructor, which creates an empty album music collection. Alsooverload the assignment operator and implement the destructor and copy constructor.‚Ä¢ Implement the add and remove music album functions whose details are given below:Add a music album: This function adds a music album to the collection. The artist, the title andthe year are specified as parameters. In this collection, the pair of artist and title are unique(however, there can be multiple albums of the same artist and multiple albums with the sametitle). Thus, if the user attempts to add a music album with an already existing artist and title, donot add the music album and return false. Do not display any warning messages. Otherwise,if the album does not exist in the collection, add it to the collection and return true.#ifndef __SIMPLE_MAC_H#define __SIMPLE_MAC_H#include &lt;string&gt;using namespace std;#include “SimpleMusicAlbum.h”class MAC{public:MAC();~MAC();MAC(const MAC &amp;macToCopy);void operator=(const MAC &amp;right);bool addMusicAlbum(const string maArtist,const string maTitle,const int maYear);bool removeMusicAlbum(const string maArtist,const string maTitle);int getMusicAlbums(MusicAlbum *&amp;allMusicAlbums);private:MusicAlbum *musicAlbums;int noOfMusicAlbums;};#endifRemove a music album: This function removes a music album from the collection. The artistand the title are specified as parameters. If the given album exists in the collection, remove itfrom the collection and return true. Otherwise, if there is no album with the given artist andtitle, do not perform any action and return false. Likewise, do not display any warningmessages.‚Ä¢ Implement the get function for music albums. The getMusicAlbums function should returnthe number of the music albums in the collection using the return value and the music albumsin the collection by a pass-by-reference parameter called allMusicAlbums. Do not forget toput a deep copy of the musicAlbums to the pass-by-reference parameter; otherwise, you mayencounter run-time errors.‚Ä¢ Do not delete or modify any part of the given data members or member functions. However,you may define additional functions and data members, if necessary.3. To test Part A, you should code your own main function in a separate file. Do not forget to test yourcode for different cases. However, do not submit any file containing the main function; otherwise,you may lose a considerable number of points. We will code our own driver to grade Part A of yourassignment. In doing that, we will use the get functions of the MusicAlbum and MAC classes. Thus,do not forget to implement the get functions of these two classes.Below is an example of the test code and its output. In this example code, there is a global functioncalled displayAllMusicAlbums. We will use it to display the music albums in the collectionand to understand whether you add/remove music albums correctly. If you want, you may use thisglobal function for your tests as well. Notice that the last two lines of this global function are todeallocate the allMusicAlbums array. Do not remove these two lines if you get any run-timeerrors while using the function. If you have such run-time errors, most probably, you made an errorin implementing either the getMusicAlbums function or one or more of the destructor, copyconstructor, and overloaded assignment operator.#include &lt;iostream&gt;using namespace std;#include “SimpleMusicAlbum.h”#include “SimpleMAC.h”void displayAllMusicAlbums(MAC mac){MusicAlbum *allMusicAlbums;int noOfMusicAlbums = mac.getMusicAlbums(allMusicAlbums);cout &lt;&lt;“No of music albums: “&lt;&lt; noOfMusicAlbums &lt;&lt; endl;for (int i = 0; i &lt; noOfMusicAlbums; i++){cout &lt;&lt; allMusicAlbums[i].getMusicAlbumArtist() &lt;&lt;“, ”&lt;&lt; allMusicAlbums[i].getMusicAlbumTitle() &lt;&lt;” (”&lt;&lt; allMusicAlbums[i].getMusicAlbumYear() &lt;&lt;“)”&lt;&lt; endl;}if (allMusicAlbums != NULL)delete [] allMusicAlbums;}The output should be:What to submit for Part A?You should put your SimpleMusicAlbum.h, SimpleMusicAlbum.cpp, SimpleMAC.h, andSimpleMAC.cpp files into a folder and zip the folder. In this zip file, there should not be any filecontaining the main function. The name of this zip file needs to bePartA_secX_Firstname_Lastname_StudentID.zip, where X is your section number.Then you should follow the steps that are explained at the end of this document for the submission ofPart A.What to be careful about implementation and submission for Part A?You need to read the ‚Äúnotes about implementation‚Äù and the ‚Äúnotes about submission‚Äù parts that aregiven at the end of this document.int main(){MAC m;m.addMusicAlbum(“John Coltrane”, “My Favorite Things”,1961);if (m.addMusicAlbum(“John Coltrane”, “A Love Supreme”,1965))cout &lt;&lt; “Successful insertion of John Coltrane, ”&lt;&lt; “A Love Supreme (1965)” &lt;&lt; endl;elsecout &lt;&lt; “Unsuccessful insertion of John Coltrane, ”&lt;&lt; “A Love Supreme (1965)” &lt;&lt; endl;m.addMusicAlbum(“Jethro Tull”, “Thick As A Brick”,1972);m.addMusicAlbum(“Mike Oldfield”, “Tubular Bells”,1973);m.addMusicAlbum(“Pink Floyd”, “The Dark Side of the Moon”,1973);displayAllMusicAlbums(m);if (m.removeMusicAlbum(“John Coltrane”, “Giant Steps”))cout &lt;&lt; “Successful deletion of John Coltrane, ”&lt;&lt; “Giant Steps” &lt;&lt; endl;elsecout &lt;&lt; “Unsuccessful deletion of John Coltrane, ”&lt;&lt; “Giant Steps” &lt;&lt; endl;return 0;}Successful insertion of John Coltrane, A Love Supreme (1965)No of music albums: 5John Coltrane, My Favorite Things (1961)John Coltrane, A Love Supreme (1965)Jethro Tull, Thick As A Brick (1972)Mike Oldfield, Tubular Bells (1973)Pink Floyd, The Dark Side of the Moon (1973)Unsuccessful deletion of John Coltrane, Giant StepsPART B: (70 points)Now, Part A is to be extended such that each music album has a list of songs. The full functionality ofthis extended MAC system is to be provided. In order for this to be done, the MusicAlbum classneeds to be extended such that it additionally keeps the list of songs contained. The song list of a musicalbum must be kept in a dynamically allocated array of Song objects. Note that the number of songscan be different from one music album to another, but is normally fixed for a particular music album.The details of the classes are given below.1. The requirements of the Song class are given below. The name of the class should be Song; itsinterface:should be coded in a file called Song.h and its implementation should be coded in a file calledSong.cpp.‚Ä¢ The Song class keeps the name of a song and its running length in minutes and seconds. Thename should be unique for each music album. That is, a music album cannot have multiple songswith the exact same name but different music albums may have a song with the same name.‚Ä¢ Implement your own default constructor, destructor, and copy constructor, and overload theassignment operator.‚Ä¢ Do not delete or modify any part of the given data members or member functions. However,you may define additional functions and data members, if necessary.#ifndef __SONG_H#define __SONG_H#include &lt;string&gt;using namespace std;class Song {public:Song(const string sName = “”, const int sMins = 0,const int sSecs = 0);~Song();Song(const Song &amp;songToCopy);void operator=(const Song &amp;right);private:string name;int mins;int secs;};#endif2. The requirements of the MusicAlbum class are given below. The name of the class should beMusicAlbum. This time, the interface for the class:should be coded in a file called MusicAlbum.h and its implementation should be coded in a filecalled MusicAlbum.cpp.‚Ä¢ The MusicAlbum class is similar to the one given in Part A. However, now it should keep adynamic array of Song objects as well. Similar to Part A, you should implement your own defaultconstructor, destructor and copy constructor, and do not forget to overload the assignmentoperator. Also, you should make sure to implement get functions for the Artist, Titleand Year data members since they will be used to test your program.‚Ä¢ Your class should have a public member function called calculateMusicAlbumLength whichwill be used for testing. This function should calculate the running length of the music albumupon which it is invoked by summing up the lengths of its songs in minutes and seconds. Therunning length of the music album should be returned through pass-by-reference parameterscalled minutes and seconds. Note that in implementing this function, you should use thefact that 1 minute is 60 seconds.‚Ä¢ Do not delete or modify any part of the given data members or member functions. However,you may define additional functions and data members, if necessary.#ifndef __MUSIC_ALBUM_H#define __MUSIC_ALBUM_H#include &lt;string&gt;using namespace std;#include “Song.h”class MusicAlbum {public:MusicAlbum(const string maArtist = “”,const string maTitle = “”,const int maYear = 0);~MusicAlbum();MusicAlbum(const MusicAlbum &amp;maToCopy);void operator=(const MusicAlbum &amp;right);string getMusicAlbumArtist();string getMusicAlbumTitle();int getMusicAlbumYear();void calculateMusicAlbumLength(int &amp;minutes, int &amp;seconds);private:string artist;string title;int year;Song *songs;int noSongs;};#endif3. Below is the required part of the MAC class that you will code in Part B of this assignment. The nameof the class should be MAC; the interface for the class:should be coded in a file called MAC.h and its implementation should be coded in a file calledMAC.cpp.‚Ä¢ The MAC class is similar to the one given in Part A. However, now it should also keep the list ofsongs for each music album. Similar to Part A, you should implement your own defaultconstructor, destructor and copy constructor, and overload the assignment operator. Also youshould make sure to implement the getMusicAlbums function, as explained before.‚Ä¢ Implement the following functions that your extended system should support.Add a music album: This function adds a music album to the collection. The artist, the title andthe year are specified as parameters. In this function, the song list is not specified; the song(s)will be added later. In the music album collection, the pair of artist and title are unique (however,there can be multiple albums of the same artist and multiple albums with the same title). Thus,if the user attempts to add a music album with an already existing artist and title, do not addthe music album and return false. Do not display any warning messages. Otherwise, if thealbum does not exist in the collection, add it to the collection and return true. This function issimilar to what you will have implemented in Part A. But, in Part B, you should also create anempty song list for the music album when you add it to the collection.#ifndef __MAC_H#define __MAC_H#include &lt;string&gt;using namespace std;#include “MusicAlbum.h”class MAC{public:MAC();~MAC();MAC(const MAC &amp;macToCopy);void operator=(const MAC &amp;right);bool addMusicAlbum(const string maArtist,const string maTitle,const int maYear);bool removeMusicAlbum(const string maArtist,const string maTitle);int getMusicAlbums(MusicAlbum *&amp;allMusicAlbums);bool addSong(const string maArtist, const string maTitle,const string sName, const int sMins,const int sSecs);bool removeSongs(const string maArtist,const string maTitle);void calculateAvgMusicAlbumLength(int &amp;minutes,int &amp;seconds);private:MusicAlbum *musicAlbums;int noOfMusicAlbums;};#endifRemove a music album: This function removes a music album from the collection. The artistand the title are specified as parameters. If the given album exists in the collection, remove itfrom the collection and return true. Otherwise, if there is no album with the given artist andtitle, do not perform any action and return false. Likewise, do not display any warningmessages. Note that this function should also clear the song list of the specified music album.This function is similar to what you will have implemented in Part A. But now, for Part B, youshould also remove the song list when you remove the music album from the collection.Add a song to the music album: This function adds a song to the song list of a music album inthe collection. The artist, the title and the year together with the name and the running lengthof the song in minutes and seconds are specified as parameters. In this function, you should takecare of the following issues:o If the specified music album does not exist in the collection, do not perform any actionand return false. Do not display any warning messages.o All song names are unique in a music album. Thus, if the user attempts to add a song withan existing name for the specified music album, do not perform any action and returnfalse. Do not display any warning messages. (However, different music albums mayhave a song with the same name.)o Otherwise, add the song to the song list of the specified music album and return true.Remove song list from the music album: This function clears the song list of a music album.The artist and the title are given as parameters. If there is no music album with the specifiedartist and title, or if there are no songs in the song list, do not perform any action and returnfalse. Do not display any warning messages. Otherwise, clear the song list of the specifiedmusic album and return true.Calculate the average running length of music albums in the collection: This functioncalculates the average running length of all music albums in the collection in minutes andseconds and returns the result through pass-by-reference parameters called minutes andseconds. Note that in implementing this function you should resort to thecalculateMusicAlbumLength function of the MusicAlbum class and use the fact that1 minute is 60 seconds. If there are no music albums in the collection, or all music albums haveempty song lists, this function should return 0 minutes and 0 seconds.‚Ä¢ Do not delete or modify any part of the given data members or member functions. However,you may define additional functions and data members, if necessary.