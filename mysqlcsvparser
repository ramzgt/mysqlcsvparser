package mysqlcsvparser;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.IOException;
import java.io.File;
import java.io.FileWriter;
import javax.swing.*;
import java.util.ArrayList;

public class MySQLCSVParser {
    
    public BufferedReader br;
    public File f;
    public ArrayList feed;
    
    public static void main(String[] args) {
        MySQLCSVParser newParser = new MySQLCSVParser();
    }
    
    public MySQLCSVParser(){
        feed = new ArrayList();
        fileOpen();
        readLines();
    }
    
    public void fileOpen(){
        try {
            JFileChooser fc = new JFileChooser();
            fc.showOpenDialog(fc);
            f = fc.getSelectedFile();
            br = new BufferedReader(new FileReader(f));     
        } catch (IOException e) {
            System.err.println("Could not read file");
            System.exit(-1);
        }
    }
    
    public void readLines(){
        try{
        String outp = "";
        String parsed = "";
        //String meow[] = new String[7];//standard string array we swap with
        File file = new File(f.getAbsolutePath()+"_MYSQLCSV");
        file.createNewFile();
        
        BufferedWriter bw = new BufferedWriter(new FileWriter(file));
        
        int linecount = 1;
        
            while ((outp = br.readLine()) != null ) {
                outp = outp.replace("'", "");//replace all stray quotes
                outp = outp.replace("\"" , "");
                String[] meoow = outp.split(",");
                if (meoow.length > 7){// figure out how to deal with the extra commas
                    System.out.println("bad line at: " + linecount);
                }
                outp="";
                boolean firstTimeRun = true;
                for(String m: meoow){
                    if (firstTimeRun){ 
                        outp += m+","; // no need for quotes on ID number
                        firstTimeRun = false;
                    }
                    else{
                    outp += "'"+m+"'"+",";//add ridiculous quotation marks
                    }
                }
                outp = outp.substring(0, outp.length()-1);//take off last comma
                parsed = "(" + outp + "),";
                System.out.println(parsed);
                bw.write(parsed);
                bw.newLine();      
            linecount++;    
            }
            br.close();
            bw.close();
        }
        catch(IOException e){
            System.out.println("error");
        }
    }
    
}
