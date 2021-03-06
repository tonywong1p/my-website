<template>
  <v-card class="grey lighten-3 animated fadeIn">
    <div class="gradient darken-1">
      <v-layout wrap style="position:relative;top:30px">
        <v-flex xs12 d-flex justify-center align-center>
          <div style="text-align:center" class="white--text pb-5">
            <h3 class="display-1 mb-2">Resume</h3>
          </div>
        </v-flex>
      </v-layout>
    </div>
    <v-card-title class="px-3">
      <v-layout wrap>
        <v-flex xs12 lg6 class="mt-2">
          <h3 class="headline">Experience</h3>
          <v-timeline dense class="hidden-xs-only">
            <v-timeline-item v-for="experience in experiences" :key="experience.id" left small color="orange lighten-2">
              <v-card class="elevation-2 mr-3">
                <v-card-title>
                  <div>
                    <span class="title mb-1">{{experience.title}}</span><br>
                    <span class="grey--text"><span class="blue--text">{{experience.year}}</span> <span class="mx-1">|</span>{{experience.company}}</span>
                  </div>
                </v-card-title>
                <ul class="mx-2 pb-4">
                  <li v-for="(duty,index) in experience.duties" :key="index">{{duty}}</li>
                </ul>
              </v-card>
            </v-timeline-item>
          </v-timeline>
          <v-timeline dense align-top class="hidden-sm-and-up">
            <v-timeline-item v-for="experience in experiences" :key="experience.id" left small color="orange lighten-2">
              <v-layout column>
                <div>
                  <span class="title mb-1">{{experience.title}}</span><br>
                  <span class="grey--text"><span class="blue--text">{{experience.year}}</span> <span class="mx-1">|</span>{{experience.company}}</span>
                </div>
                <ul class="mx-2 pb-4">
                  <li v-for="(duty,index) in experience.duties" :key="index">{{duty}}</li>
                </ul>
              </v-layout>
            </v-timeline-item>
          </v-timeline>
        </v-flex>
        <v-flex xs12 lg6 class="mt-2">
          <h3 class="headline">Education</h3>
          <v-timeline dense class="hidden-xs-only">
            <v-timeline-item v-for="(education,index) in educations" :key="index" left small color="orange lighten-2">
              <v-card class="elevation-2 mr-3">
                <v-card-title>
                  <div>
                    <span class="title mb-1" v-if="index!=2">{{education.title}}</span>
                    <a class="title mb-1" v-if="index==2" href="https://www.freecodecamp.org/certification/tonywong1p/javascript-algorithms-and-data-structures" target="_blank">{{education.title}}</a>
                    <br>
                    <span class="grey--text"><span class="blue--text">{{education.year}}</span> <span class="mx-1">|</span>{{education.institution}}</span>
                  </div>
                </v-card-title>
                <ul class="ml-2 pb-4">
                  <li v-for="(course,index) in education.courses" :key="index">{{course}}</li>
                </ul>
              </v-card>
            </v-timeline-item>
          </v-timeline>
          <v-timeline dense align-top class="hidden-sm-and-up">
            <v-timeline-item v-for="education in educations" :key="education.id" left small color="orange lighten-2">
              <v-layout column>
                <div>
                  <span class="title mb-1">{{education.title}}</span><br>
                  <span class="grey--text"><span class="blue--text">{{education.year}}</span> <span class="mx-1">|</span>{{education.company}}</span>
                </div>
                <ul class="mx-2 pb-4">
                  <li v-for="(course,index) in education.courses" :key="index">{{course}}</li>
                </ul>
              </v-layout>
            </v-timeline-item>
          </v-timeline>
        </v-flex>
      </v-layout>
      <v-layout column>
        <v-layout wrap>
          <v-flex xs12 sm6 md6 lg4 class="px-4 mt-3" order-xs2 order-lg1>
            <h3 class="headline">Coding <span class="blue--text">Skills</span></h3>
            <div class="mt-2" v-for="(codingSkill,i) in codingSkills" :key="i">
              <span class="caption">{{codingSkill.title}}</span><br>
              <span class="subheading">{{codingSkill.text}}</span>
              <v-progress-linear :value="codingSkill.value" color="warning"></v-progress-linear>
            </div>
          </v-flex>
          <v-flex xs12 sm12 md12 lg4 order-xs1>
            <radar-chart></radar-chart>
          </v-flex>
          <v-flex xs12 sm6 md6 lg4 class="px-4 mt-3" order-xs3 order-lg2>
            <h3 class="headline">Design
              <span class="blue--text">Skills</span>
            </h3>
            <div class="mt-2" v-for="(designSkill,i) in designSkills" :key="i">
              <span class="caption">{{designSkill.title}}</span><br>
              <span class="subheading">{{designSkill.text}}</span>
              <v-progress-linear :value="designSkill.value" color="warning"></v-progress-linear>
            </div>
          </v-flex>
        </v-layout>
        <v-layout justify-center class="mb-3">
          <v-btn target="_blank" :href="resume">Download Resume</v-btn>
        </v-layout>
      </v-layout>
    </v-card-title>
  </v-card>
</template>

<script>
  import radarChart from '@/components/radarChart.vue';
  export default {
    components: {
      radarChart
    },
    data() {
      return {
        resume: require('@/assets/Resume_TonyWongSiuFai_2019.pdf'),
        experiences: [{
            title: 'IT Project Manager',
            company: 'Edvant Company Limited',
            year: 'Jun. 2015 to Dec. 2018',
            duties: ['Managed 8 cross-functional IT projects under the scope of campus-wide usage in local and south-Asian universities by collaborating with engineers, channel partners and systems integrators.',
              'Achieved 1.8+ million sales revenue over 2 years by promoting cloud-based solutions and tailor-made software products with strong stakeholder management.',
              'Developed front-end interfaces of web applications hands-on for software production.'
            ]
          },
          {
            title: 'Research Assistant',
            company: 'CLEAR, Chinese University of Hong Kong',
            year: 'Dec. 2014 to May 2015',
            duties: ['Created a hardware prototype of single-board server having local Wi-Fi network for supporting the usage of web applications in internet-isolated environment.',
              'Investigated network control technique by constructing local DNS, firewall rules, and proxy server.',
            ]
          },
          {
            title: 'Co-founder and Tutor',
            company: 'Y&F Tutorial Center',
            year: 'Sept. 2013 to Jun. 2016',
            duties: ['Supervised 100+ students aging from primary to secondary school in acquiring better understanding of targeted weak areas within the subject.',
              'Managed stakeholders including place owner, parents and tutors in day-to-day operation.',
              'Executed promotion campaigns to improve business exposure and revenue by over 80%.'
            ]
          }
        ],
        educations: [{
          title: 'MSc in Information and Technology Management',
          institution: 'Chinese University of Hong Kong',
          year: 'Sept. 2017 to Mar. 2019',
          courses: ['Honored with Second-Upper Class Division',
            'Coursework includes: Project Management, Database & Big Data Management, Cyber Security, Information System Analysis and Auditing, IT Law, Business Intelligence',
            'Cumulative GPA: 3.344/4'
          ]
        }, {
          title: 'Developer Certification, JavaScript Algorithms and Data Structures',
          institution: 'FreeCodeCamp.org',
          year: 'Feb. 2017 - Jun. 2018',
          courses: [
            'Coursework includes: Object-oriented Programming, Functional Programming, JavaScript Algorithms Scripting and Data Structures',
            'Representing approximately 300 hours of course work'
          ]
        }, {
          title: 'BEng in Electronic Engineering',
          institution: 'Chinese University of Hong Kong',
          year: 'Sept. 2011 to Jul. 2015',
          courses: ['Honored with Third Class Division',
            'Coursework includes: Engineering Design, Advanced Engineering Math, Analog Integrated Circuits, Biomedical Modelling, Random Processes & DSP, Computing Using C++',
            'Final Year Project: Depth reconstruction from several 2D images, Grade A-',
            'Cumulative GPA: 2.114/4 | Major GPA: 2.452/4'
          ]
        }],
        codingSkills: [{
          title: 'Web language',
          text: 'HTML, CSS, JavaScript',
          value: 95
        }, {
          title: 'Front-end Framworks',
          text: 'Vue.js, Angular.js, Bootstrap, Material Design',
          value: 90
        }, {
          title: 'Back-end Frameworks',
          text: 'Node.js, Nginx, MySQL, MongoDB',
          value: 75
        }, {
          title: 'Others',
          text: 'Nginx, Git, Python',
          value: 70
        }],
        designSkills: [{
          title: 'Graphic Design',
          text: 'Adobe Illustrator, Photoshop',
          value: 90
        }, {
          title: '3D Design',
          text: 'Blender, AutoCAD',
          value: 80
        }, {
          title: 'Audio Design',
          text: 'Logic Pro, Adobe Audition',
          value: 80
        }, {
          title: 'Video Editing',
          text: 'Premiere Pro',
          value: 75
        }]
      }
    }
  }
</script>
