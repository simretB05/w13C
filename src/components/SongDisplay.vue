<template>
    <section>
        <h1>Best of 80's Hits Collections by Various Artists ...</h1>
            <div class="container">
                <div class="main_card">
                    <article v-for="(song, i) in songs" :key="i" >
                        <h2 @click="select_song">{{song[`title`]}}</h2>
                        <p> Artist Name:{{song[`artist`]}}</p>
                        <p>song ID:{{song[`song_id`]}}</p>
                        <img :src="song[`image_url`]" alt="song album image">
                    </article>
                </div>
                <div class="sellection">
                    <h1 class="sellection_title">Currently playing song</h1>
                    <p v-if="noSelectedSongs">{{noSelectedSongs}}</p>
                    <div v-else class="now_playing">
                        <h2 @click="select_song">{{displaySongTitle}}</h2>
                        <p> Artist Name:{{ displaySongTitle}}</p>
                        <p> song ID:{{ displaySongId}}</p>
                        <img :src="displayimage_url" alt="song album image">

                    </div>
                  

                </div>
            </div>
        
    </section>
</template>
<script>
    export default {
        data() {
            return {
                noSelectedSongs: ' Please select a song!',
                displaySongTitle: '',
                displaySongArtist: '',
                displaySongId: '',
                displayimage_url:'No Image',
                selectedSongs: [],
                songs:[
                        {
                            title: "Billie Jean",
                            artist: "Michael Jackson",
                            song_id: "123",
                            image_url:"https://i.ytimg.com/vi/gZRFJyeJLAM/maxresdefault.jpg"
                        },
                        {
                            title: "Sweet Child o' Mine",
                            artist: "Guns N' Roses",
                            song_id: "456",
                            image_url: "https://yt3.googleusercontent.com/XYdITfFzeQBLoNsIIpthkC1jfK9r-jVijx_ULuralq1KaN35Z_tJdgyoB9O-eSCm_NdEgN1E-Ok=s900-c-k-c0x00ffffff-no-rj"
                        },
                        {
                            title: "Like a Prayer",
                            artist: "Madonna",
                            song_id: "789",
                            image_url: "https://i.ytimg.com/vi/IlPCW6nLheM/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLDFG0GI5nVGiefJK1PwGAW_prr6UA"

                        },
                        {
                            title: "Livin' on a Prayer",
                            artist: "Bon Jovi",
                            song_id: "1011",
                            image_url: "https://i.ebayimg.com/images/g/JNIAAOSw62hjGSQb/s-l1600.jpg"

                        },
                        {
                            title: "Take On Me",
                            artist: "a-ha",
                            song_id: "1213",
                            image_url: "https://i.ytimg.com/vi/djV11Xbc914/maxresdefault.jpg"
                        }
                    ]
                }
        },
    methods: {
            select_song: function ( details ){
            let get_title = details[`target`].innerText;
            for ( let i = 0; i < this.songs.length; i++ ){
                if ( get_title===this.songs[i][`title`]){
                    this.displaySongTitle=this.songs[i][`title`]
                    this.displaySongArtist = this.songs[i][`artist`]
                    this.displaySongId = this.songs[i][`song_id`]
                    this.displayimage_url = this.songs[i][`image_url`]
                    this.noSelectedSongs = ''
                   
                    break
                    
                }
                }
                    
            }
          
        },
       
    }
         
</script>

<style scoped>
section{
    display:grid;
    place-items: center;
    min-height: 80vh;
    

}
.container{
    display:grid;
    place-items: center;
    min-height: 80vh;
    width: 100%;
    grid-template-columns:  1fr 1fr;
}
h1{
    color:rgb(29, 132, 234);
    justify-self: start;
    font-size: 2rem;
}


.main_card{
    display:grid;
    place-items: center;
    min-height: 100vh;
    gap:16px;

}

article{
    display:grid;
    place-items: center;
    background-color: lightblue;
    width: 90%;
    padding: 16px;
    min-height: 30%;
    grid-template-columns: 1fr 1fr 1fr;
}
img{
    width:100px;
}
p{
    text-align: start;
    padding: 6px;
    font-weight: 700;

}
.sellection{
    min-height: 100vh;
    align-self: start;

}
.sellection_title{
font-size: 3rem;
    width: 100%;
}
.sellection_title ~p{
    font-size: 2rem;

}
.selected_songs{
     font-size: 1.3rem;
     color: green;
}
.now_playing{
place-items: center;
background-color: papayawhip;
grid-template-columns: 1fr 1fr 1fr;
}

</style>