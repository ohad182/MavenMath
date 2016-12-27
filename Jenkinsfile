pipeline {
    agent label:'pt-lt0582'
    stages {
        stage ('Delete old file')
        {
            steps {
                bat '''
                del /q "c:\\logs\\jenkins\\*.csv"
                del /q "c:\\logs\\jenkins\\*.html"
                del /q "c:\\logs\\jenkins\\*Finish*"
                del /q "c:\\logs\\jenkins\\*.xml"
                '''
                }
        }

        stage ('Kill Old GRAS')
        {
	steps{
            bat 'taskkill /f /im GRAS.exe'
	    }
        }

        stage ('Run GRAS')
        {
		 steps {
            bat 'cd "c:/Program Files (x86)/Marvell/GRAS"'

            bat 'GRAS.exe "C:/work/TestCI.xml" -s -jo "c:/logs/jenkins" -jv cisco_tesla_bx_v2.3 -dp'
			}
        }
    }
}
